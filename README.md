# DisturbedYoutubeVideoDetection
by Bianca Ortega , A’nya Carr , Andrea Balcacer
<details>
<summary>Table of Contents</summary>
  
1. [Summary](#summary)
2. [Features](#features)
3. [Visuals](#visuals)
4. [Technologies](#technologies)
5. [What I Learned](#what-i-learned)
6. [Setup and Installation](#setup-and-installation)
7. [Usage](#usage)
8. [Code Examples](#code-examples)
9. [How to Contribute](#how-to-contribute)
10. [License](#license)
11. [Contact](#contact)
12. [Acknowledgments](#acknowledgments)

</details>

## Summary

This program uses Supervised Image Classification and NLP to analayze and assess whether a Youtube Video is suitable for children based on Image Captures and Video Subtitles.

We recognize that more children are using the internet, often times not fully under supervision. Without guidance, children can be exposed to inappropriate and disturbing media that can affect their emotional state, feeling of safety and more. Youtube is a large-scale platform that contains various kinds of videos and due to its global popularity, children enjoy this app. The danger lies in how well the app does that protecting children from their adult and potentially harmful content, with multiple studies finding more disturbing videos circulating the app's children genre.


## Features
- **Image Classification**:
  - Video Frames were extracted from Youtube Videos using PyTorch,PyTube and OpenCv-Python and storing them in a Google Folder. Frames were generated every 17 seconds for Suitable Videos, 30 seconds for Disturbed due to the Suitable Videos video duration were generally shorter than the Disturbed Videos
    
  - Model: VGG-16
  - Dataset: 1,945 Frames Total= 829 suitable + 1,115 disturbed
  - Parameters: Cross Entropy loss, learning rate: 0.001
  - Classes: 0 (Disturbed) , 1 ( Suitable)
  
- **Natural Language Processing**:
  - Captions were extracted from Youtube video using Youtube Data API, stored in a Google Folder and accessed through Google Collaboratory. Some limitations were that some videos were excluded that did not have captions avaliable due to: *No captions were set by Creator, Disabled, No English Captions Avaliable, Incomprehenisble Words and other cases*. The captions were ran through an LSTM model that would give us a percentage of how many words in the transcript belonged to the classes: Suitable, Disturbed. Word Bank was compiled by using a list of Youtube flagged words and ChatGPT generated Safe words for children.
    
  - Model: Long Short Term Memory Recurrent Neural Network 
  - Dataset: 50 Video Captions + Keyword Word Bank 616 suitable words + 743 disturbed words
  - Parameters: Cross Entropy loss, dropout: 0.50
  - 
- **Video Metadata Extraction**:
  - Youtube Video Links, Title, and Captions extracted from Youtube Videos using Youtube Data API
 
  - Video Links were extracted from community flagged Youtube Channels with disturbed/ inapporiate content and appropriate content for children using Youtube Data API. Some limitations were that we did not include many Youtube Shorts as many of them did not have captions and some had a different link layout than full videos. Some links deactivated during the process, making them unusable. We stuck to 50 videos, 25 for each class as to gather alot of data but also conserve Google storage usage. Additonally, to reduce bias, we limited videos we chose from a channel.


## Visuals
*Insert images or gifs showing your project in action. Consider before/after shots, workflows, or demos.*

*Example of a Caption Textfile*
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/42509844-97d9-480f-86ae-c8b914278e5a)

*Example of Suitable Frame*
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/88bf8532-cf63-4e8f-a312-5e3769915569)

*Example of Disturbed Words*
<details>
  <summary>Warning: Contains Curses,Inapproriate Phrases</summary>

<img width="179" alt="image" src="https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/fca8df47-a6a4-4a73-819e-9159a714e41e">
</details>

*Example of Disturbed Frame*
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/3036a2b5-97f0-4668-9c4d-2178f0de6d67)

*Example of Suitable Words*
<img width="96" alt="image" src="https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/c0ac4a00-fff9-4496-a804-42aa641103fc">

*Suitable/Disturbed Word in Caption LSTM Confusion Matrix*
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/aa4e2be0-8972-4d84-a682-ba914f39be9b)
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/f419a57d-3ace-4205-839c-41f62a2e30e3)

*Classifying Images from Suitable and Disturbed Frames VGG16 Confusion Matrix and Graphs* 

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/4b2ee97c-f342-4fe8-ab3e-bb081de9c4c9)

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/f57e0e93-c554-47e3-9f54-00c5d0ec1443)

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/b4be44ae-1e6c-4e9e-b039-3c7db0ddad9b)














## Technologies
Detail the technologies, languages, frameworks, and tools used in the project.
- Technology 1
- Technology 2
- Technology 3

## What I Learned
Highlight specific skills or concepts you learned or improved upon while working on this project. This section should directly address potential employer interests.
- **Skill or Concept 1**: How you applied it in the project.
- **Skill or Concept 2**: Challenges you overcame.
- **Skill or Concept 3**: Any particular achievements or insights.

## Setup and Installation
*Provide a clear, step-by-step guide to set up the project locally.*
1. Get a Google API Key
2. Open 


## Usage
*Guide on how to use the project, include example commands or scripts.*

## Code Examples
*Show small, but significant snippets of code from your project.*

## How to Contribute
*Encourage contributions and provide guidelines for how others can help.*

## License
*State the license under which your project is available.*

## Contact
- *First and last name* - *Email address*
- *Any other contact information*

## Acknowledgments
*Credits to individuals or resources that helped you during the project.*

---
