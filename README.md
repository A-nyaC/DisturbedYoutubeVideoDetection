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

This program uses Supervised Image Classification and NLP to analayze and assess whether a Youtube Video is suitable for children based on Image Captures and Video Subtitles. We investigated these two approaches and set up implementation of a combined apporach using OpenAI CLIP.

We recognize that more children are using the internet, often times not fully under supervision. Without guidance, children can be exposed to inappropriate and disturbing media that can affect their emotional state, feeling of safety and more. Youtube is a large-scale platform that contains various kinds of videos and due to its global popularity, children enjoy this app. The danger lies in how well the app does that protecting children from their adult and potentially harmful content, with multiple studies finding more disturbing videos circulating the app's children genre.


## Features
- **Image Classification**:
  - Video Frames were extracted from Youtube Videos using PyTorch,PyTube and OpenCv-Python and storing them in a Google Folder. Frames were generated every 17 seconds for Suitable Videos, 30 seconds for Disturbed due to the Suitable Videos video duration were generally shorter than the Disturbed Videos.
    
  - Model: VGG-16
  - Dataset: 1,945 Frames Total= 829 suitable + 1,115 disturbed
  - Parameters: Cross Entropy loss, learning rate: 0.001
  - Classes: 0 (Disturbed) , 1 ( Suitable)
  
- **Natural Language Processing**:
  - Captions were extracted from Youtube video using Youtube Data API and Youtube Transcript API, stored in a Google Folder and accessed through Google Collaboratory. Some limitations were that some videos were excluded that did not have captions avaliable due to: *No captions were set by Creator, Disabled, No English Captions Avaliable, Incomprehenisble Words and other cases*. The captions were ran through an LSTM model that would give us a percentage of how many words in the transcript belonged to the classes: Suitable, Disturbed. Word Bank was compiled by using a list of Youtube flagged words and ChatGPT generated Safe words for children.
    
  - Model: Long Short Term Memory Recurrent Neural Network 
  - Dataset: 50 Video Captions + Keyword Word Bank 616 suitable words + 743 disturbed words
  - Parameters: Cross Entropy loss, dropout: 0.50
  
- **Video Metadata Extraction**:
  - Youtube Video Links, Title, and Captions extracted from Youtube Videos using Youtube Data API
 
  - Video Links were extracted from community flagged Youtube Channels with disturbed/ inapporiate content and appropriate content for children using Youtube Data API. Some limitations were that we did not include many Youtube Shorts as many of them did not have captions and some had a different link layout than full videos. Some links deactivated during the process, making them unusable. We stuck to 50 videos, 25 for each class as to gather alot of data but also conserve Google storage usage. Additonally, to reduce bias, we limited videos we chose from a channel.
 
- ** OpenAI CLIP model**:
  -   Using a demo Google Colaboratory Notebook from the CLIP GitHub repository, we intended to encode both frames and transcripts and run them through a cosine similarity archi- tecture. This process extends to zero-shot image classification, showcasing the model’s ability to classify images without prior training on particular classes.
However, it is noteworthy that the model faced challenges in properly capturing all transcripts and frames, resulting in instances where complete pairs were not available for analysis. Due to the newness of this model, and the complexity of the dataset we have created, there are a lot of steps required to format the data into a readable way for the CLIP model.

  - Most of our transcripts size went over a token limit CLIP specified, requiring us to break down the transcripts into chunks for further processing. This limitation affected the overall result generation, as the model’s capacity to derive comprehensive insights was hindered by incomplete data. Despite these challenges, the sections of the dataset successfully processed provide valuable insights into the model’s performance, shedding light on the potential efficacy of the multimodal fusion strategy.


## Visuals
*Insert images or gifs showing your project in action. Consider before/after shots, workflows, or demos.*

*Example of a Caption Textfile*
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/42509844-97d9-480f-86ae-c8b914278e5a)

*Example of Suitable Frame*
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/88bf8532-cf63-4e8f-a312-5e3769915569)

*Example of Disturbed Words and Frame*

<details>
  <summary>Warning: Contains Curses,Inapproriate Phrases</summary>
<img width="179" alt="image" src="https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/fca8df47-a6a4-4a73-819e-9159a714e41e">

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/3036a2b5-97f0-4668-9c4d-2178f0de6d67)
</details>

*Example of Suitable Words*
<img width="96" alt="image" src="https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/c0ac4a00-fff9-4496-a804-42aa641103fc">

*Suitable/Disturbed Word in Caption LSTM Confusion Matrix*
![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/aa4e2be0-8972-4d84-a682-ba914f39be9b)

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/f419a57d-3ace-4205-839c-41f62a2e30e3)

*Classifying Images from Suitable and Disturbed Frames VGG16 Confusion Matrix and Graphs* 

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/4b2ee97c-f342-4fe8-ab3e-bb081de9c4c9)

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/f57e0e93-c554-47e3-9f54-00c5d0ec1443)

![image](https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/b4be44ae-1e6c-4e9e-b039-3c7db0ddad9b)

 *CLIP Frame + Transcript Pairing Example

 <img width="720" alt="image" src="https://github.com/A-nyaC/DisturbedYoutubeVideoDetection/assets/171085427/5e0158b2-bda6-4cc1-b312-f6f9757a5809">

## Technologies
- Google Collab
- Python
- PyTorch
- Youtube Data API, Youtube Transcript API
- OpenAI CLIP
- https://www.youtube.com/watch?v=SwSbnmqk3zY

## What I Learned
Highlight specific skills or concepts you learned or improved upon while working on this project. This section should directly address potential employer interests.
- **Dataset Creation**: I experimented with creating a dataset that is balanced. One, we set a time interval to limit how many frames we will create, we aimed for 1,000 frames to be used for Machine Learning. I also learned that creating a dataset takes a longer time than coding. The majority of our project was gathering data due to finding a predefined dataset for our project was difficult to find. Nevertheless we were able to analyze using the dataset.
- **NLP**: I never hsd prior experience with using NLPs and was curious as to how it works. I learned that words/sentences can get broken down into tokens, specialized and reduced data, to be utilized in NLP Model. Then it can be used similarly in training. Additionally, this process showed me the uses of softmax, disabling nodes for the model to work harder to retain relevant data.
- **APIs**: I learned how to access data of an API that stores its data in a Object type, generating an API Key and navigating Object type data. This has made future projects using APIs and accessing their data easier to pick up on.

## Setup and Installation
*Provide a clear, step-by-step guide to set up the project locally.*
1. Get a Google API Key
2. Open YoutubeDisturbedClassifictionProject.ipynb
3. Insert Google API Key in the file

   
## Code Examples

# Extracting Transcripts Excerpt:
```
suitableVideoLinks = ['STf0Y51cEEc', 'ziTeTAQhyo4', 'x5RbKDaRkjM', 'GOkYIggSZqM', 'PJ57DuxwBn4', 'JSha_1TOvC0', 'IopViQfSSn0', '0PVebbCBSlk', 'YbvCmKvnwRs', 'lSMjQn3iBng']
suitableTranscripts = []
for video_id in suitableVideoLinks:
    try:
      transcript = YouTubeTranscriptApi.get_transcript(video_id)

      if transcript:
        text_list = [entry['text'] for entry in transcript]
        suitableTranscripts.append(text_list)
        print("https://www.youtube.com/watch?v="+video_id)
    except (
                VideoUnavailable,
                TooManyRequests,
                YouTubeRequestFailed,
                NoTranscriptFound,
                TranscriptsDisabled,
                NotTranslatable,
                TranslationLanguageNotAvailable,
                NoTranscriptAvailable,
                FailedToCreateConsentCookie,
                InvalidVideoId,
                ) as e:
                print("No transcript available for video:", video_id)
print("How many SuitableVideos have transcripts : ",len(suitableTranscripts))
```

# Making Frames from a video
```
                capture = cv2.VideoCapture(video_path)

                # Get the frames per second (fps) of the video
                fps = capture.get(cv2.CAP_PROP_FPS)

                # Calculate the frame interval based on the video category
                if subfolder == 'Suitable':
                    frame_interval = int(17 * fps)  # Create frames every 17 seconds
                elif subfolder == 'Disturbed':
                    frame_interval = int(30 * fps)  # Create frames every 30 seconds

```

## Contact
- Bianca Ortega- https://www.linkedin.com/in/bianca-m-ortega?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app :Image Classification, NLP Specialist, Dataset Creation, Debugging, Project Management
- A’nya Carr- https://www.linkedin.com/in/a-nya-carr-180415210/ :Image Classification, NLP, Dataset Creation, Data Extraction, Debugging
- Andrea Balcacer- https://www.linkedin.com/in/andreabalcacer?trk=public_profile_browsemap-profile :Image Classification, Dataset Creation, Organization, Data Extraction and Storage, Documentation

---
