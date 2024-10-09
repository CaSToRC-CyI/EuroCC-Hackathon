# EuroCC-Hackathon
This is a repository for content relating to the Hackathon organised by EuroCC Cyprus with the Anticancer Society of Cyprus.

# Quick start
1. `> sbatch hackathon/launch_hackathon.sub`
2. Run command ssh command shown in connection_info.txt
3. Connect to jupyter server shown in connection_info.txt
4. Code your solution 

<br>


# What you'll be given
* An excel of patient files. This can be found on the cluster under the hackathon folder in your account.
  * You'll be given a small script which reads this into a Pandas DataFrame
  * For acronym in the frequency and route fields, see first sheet of hackathon.xlsx
* A list of pdf files containing the leaflets of medicines that are in the patient files.
<br>

# What we'll expect from you at the end of this hackathon

<br>

  
## A list of the interactions you found in each patient file from the spreadsheet. 

You are expected to only list major interactions but minor ones will earn some extra points.
   
  **Major interactions**: These are interactions which the Anticancer Society has given us to test your solutions. These will give you the majority of points.
  **Minor interactions**: These are interactions which you may find in the medicine leaflets stating something along the lines of "speak with your doctor if you are taking Y medicine along with X". These should **not** be marked as a major interaction.
  
  **Bonus points** for explained interactions. (e.g The two sedatives Oxycodone and Morphine shouldn't be consumed together because of their additive effects). 
  
  The format of your submission we expect looks like this (json):
     
  ```
  { "PATIENT 2": [
                    { "interaction":["tramadol","pregabalin"],
                      "severity":"Major",
                      "explanation":"Using narcotic pain medications together with other medications that cause central nervous system depression can lead to respiratory distress, coma, and even death."
                    },
                    { "interaction":["X","Y"],
                      "severity":"Minor",
                      "explanation":"There were no major interactions found in the dataset, however for medicine X it is suggested to consult with your doctor if taking X and Y together.
                    }
                  ]
    "PATIENT 3": [...]
    }
  ```
  
  In the case above the major interaction was correctly detected and explained, the next one is a minor interaction which will act as a warning.
  
  If you try to check for all combination in a patient file, you'll need to check for a huge number of combinations. 
  
  Specifically <img src="https://www.inchcalculator.com/wp-content/uploads/2020/12/combinations-formula.png" alt="n-choose-r" width="200"/> where n = number of medicines and r = number of samples. This method will significantly slow down your code and might give you a lot of false positives. So you need to make sure your retrieval and prompts are designed in such a way to limit your requests.
  
<br>


## Your source code for generating your results.
   
  We prefer a script that will read through the the excel spreadsheet we provided and generate the answers in the format above, saving it to a json file.
  
  ****This should be submited by Sunday 13/10/2024 at 23:59!****

## A presentation on Monday showcasing and explaining your solution

Winner will be announced in the near future when we evaluate your results.

<br>



# Useful resources

[Langchain:](https://python.langchain.com/v0.2/docs/introduction/) Useful for creating LLM prompt chains

[Langgraph:](https://langchain-ai.github.io/langgraph/tutorials/introduction/) Useful for debugging your chains

[Langgsmith:](https://docs.smith.langchain.com/) Useful for creating complex graph prompts

<br>

# Model limitations
You will be limited to **only** use these models:
* gemma2:27b 	(Google)
* llama3.1:latest	(Meta)
* phi3.5:3.8b-mini-instruct-fp16	(Microsoft)
* nemotron-mini:4b-instruct-fp16	(Nvidia)
  
**be considerate of your context length as to not overflow to CPU memory**

<br>

# Hardware available per team:

1 GPU - 32GB V100 from NVIDIA

10 CPU cores

40 GB RAM

<br>

# For expanding your medicine dataset

https://www.drugs.com/

https://www.medscape.com/pharmacists

https://www.nhs.uk/ 

https://go.drugbank.com/drug-interaction-checker#results

    
