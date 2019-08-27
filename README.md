

```python
import speech_recognition as sr 
  
AUDIO_FILE = ("Recording.wav") 
  
# use the audio file as the audio source 
  
r = sr.Recognizer() 
  
with sr.AudioFile(AUDIO_FILE) as source: 
    #reads the audio file. Here we use record instead of 
    #listen 
    audio = r.record(source)   
  
try: 
    print("The audio file contains: " + r.recognize_google(audio)) 
  
except sr.UnknownValueError: 
    print("Google Speech Recognition could not understand audio") 
  
except sr.RequestError as e: 
    print("Could not request results from Google Speech  Recognition service; {0}".format(e))
```

    The audio file contains: Om Bhur Bhuva Swaha Tat savitur varenyam bhargo Devasya dhimahi dhiyo yonah prachodayat
    


```python
AUDIO_FILE = ("recTwo.wav") 
  
# use the audio file as the audio source 
  
r = sr.Recognizer() 
  
with sr.AudioFile(AUDIO_FILE) as source: 
    #reads the audio file. Here we use record instead of 
    #listen 
    audio = r.record(source)   
  
try: 
    print("The audio file contains: " + r.recognize_google(audio)) 
  
except sr.UnknownValueError: 
    print("Google Speech Recognition could not understand audio") 
  
except sr.RequestError as e: 
    print("Could not request results from Google Speech  Recognition service; {0}".format(e))
```

    The audio file contains: Om Namah Shivay
    


```python
mic_list = sr.Microphone.list_microphone_names() 
mic_list
```




    ['Microsoft Sound Mapper - Input',
     'Microphone (Realtek Audio)',
     'Microsoft Sound Mapper - Output',
     'Speakers / Headphones (Realtek ',
     'Speakers (Realtek HD Audio output)',
     'Microphone (Realtek HD Audio Mic input)',
     'Stereo Mix (Realtek HD Audio Stereo input)']




```python
sample_rate=48000
chunk_size=4096
```


```python
with sr.Microphone(device_index = 0, sample_rate = sample_rate,  chunk_size = chunk_size) as source: 
    #wait for a second to let the recognizer adjust the  
    #energy threshold based on the surrounding noise level 
    r.adjust_for_ambient_noise(source) 
    print ("Say Something")
    #listens for the user's input 
    audio = r.listen(source) 
          
    try: 
        text = r.recognize_google(audio) 
        print ("you said: " ,text )
      
    #error occurs when google could not understand what was said 
      
    except sr.UnknownValueError: 
        print("Google Speech Recognition could not understand audio") 
      
    except sr.RequestError as e: 
        print("Could not request results from Google  Speech Recognition service; {0}".format(e))
```

    Say Something
    you said:  Bhur Bhuva Swaha Tat savitur varenyam bhargo Devasya dhimahi dhiyo yonah prachodaya Om Bhur Bhuva Swaha
    


```python
gayatri_mantra='Om Bhur Bhuva Swaha Tat savitur varenyam bhargo Devasya dhimahi dhiyo yonah prachodayat'
```


```python
text_arr=gayatri_mantra.split(" ")
text_arr
```




    ['Om',
     'Bhur',
     'Bhuva',
     'Swaha',
     'Tat',
     'savitur',
     'varenyam',
     'bhargo',
     'Devasya',
     'dhimahi',
     'dhiyo',
     'yonah',
     'prachodayat']




```python
s=set(text_arr)
```


```python
with sr.Microphone(device_index = 0, sample_rate = sample_rate,  chunk_size = chunk_size) as source: 
    #wait for a second to let the recognizer adjust the  
    #energy threshold based on the surrounding noise level 
    r.adjust_for_ambient_noise(source) 
    print ("Say Something")
    #listens for the user's input 
    audio = r.listen(source) 
          
    try: 
        text = r.recognize_google(audio)
        arr=text.split(" ")
        i=0
        for word in arr:
            if word not in s:
                print("You got the following word wrong :",word)
                print("It shouldve been :",text_arr[i])
            i=i+1
        
        print ("you said: " ,text )
      
    #error occurs when google could not understand what was said 
      
    except sr.UnknownValueError: 
        print("Google Speech Recognition could not understand audio") 
      
    except sr.RequestError as e: 
        print("Could not request results from Google  Speech Recognition service; {0}".format(e))
```

    Say Something
    You got the following word wrong : audio
    It shouldve been : Tat
    you said:  Om Bhur Bhuva Swaha audio
    


```python

```
