# My Voicemeter Setup :( 
This is my voicemeter that I am using. VoiceMeter Banana. Looks like this.

![alt text](https://github.com/confusedbread/VoiceMeterSetup/blob/master/VoiceBanana.PNG "Logo Title Text 1")


I use **VoiceMeterBanana** with **one virtual cable** to route **discord** through a separate channel so I can balance it separately/exclude it from **OBS**. It also allows me to split audio between my **headphones** and **speakers**/**monitors**.

# Getting Started

This is a setup for VMB (Voicemeter Banana) with one virtual-audio cable. Here how you get started. 

## Get everything you need
Go here https://vb-audio.com/Voicemeeter/banana.htm and download and run. Boom. Have a cookie🍪 You now have VMB. (Important Note This is for banana not the regular Voicementer).

Now you also need a virtual cable. Go here and download yourself a cable https://vb-audio.com/Cable/ . This virtual cable is so I can route discord away from my OBS/ balance it if I want discord to go to the stream.

Now you have VMB and one Virtual Cable.

## Setup VMB
Open VMB and familiar yourself with the important settings. The important settings you need to get right are the **hardware inputs**, **virtual inputs**, and **hardware output**. Here's a picture if you get confused. 

![alt text](https://github.com/confusedbread/VoiceMeterSetup/blob/master/VoicemeeterBananaMixerSettings.jpg "Logo Title Text 4")

This is setup we are going for here. To explain a little bit VMB uses 5 channels A1 A2 A3 B1 B2. For channels A1, A2, and A3 these are physical outputs thus, **hardward output**, like your headphones or speakers. Channels B1 and B2 are your post balanced/mixed output. B1 is the channel we want for our **OBS desktop volume**. B2 will be our isolated designated **microphone** channel. 

**Note**: for some strange reasons it's not labeled VMB but B1 IS **Output VAIO** and B2 IS **Output VAIO AUX**. Hopefully the drawing below clears things up.

```
                                    voicemeter
                     --------------------------------
main (desktop)----->| (input VAIO)			          A1|----> HeadPhones
					          |							                A2|----> Speakers
					          |							                A3|
aux (discord)------>| (input AUX)					          |
					          |				B1(output VAIO)	        |---> OBS(Desktop Audio)
						        |				B2(output AUX)	        |---> OBS(Mic/Auxiliary Audio)
						        _________________________________ 	↪ Discord Mic Input *alsoB2*
```
##### Setup Desktop Audio Input
Let's first reroute you system audio to VMB. Go to windows, look up **Sound Settings**, and open it. Now under Output make sure to select **VoiceMeter input (VB-AduioMeeter VAIO)** make sure it is not **AUX VAIO**. (I know these can be swapped. It's just for my setup main input is Desktop Audio and AUX will be discord). Here's a picture so you don't get lost.

![alt text](https://github.com/confusedbread/VoiceMeterSetup/blob/master/seleting%20audio%20windows.PNG "Logo Title Text 2")

Now in VMB in the virtual input section you should see a Voicemeeter VAIO channel/column. This is the channel that your audio is being routed to. Lets select where the audio should go. Lets select **A1** to send audio to your physical device and select **B1** to route to OBS desktop in the future. If it's a fresh install it should have A1 and B1 selected for you already. 

##### Setup Microphone Audio Input
Let's now get your microphone set up with VMB. Lets use **Hardware Input 1** for your mic. Click on **Hardware Input 1** and select your microphone (just WDM for now). Lets select **A1** to send audio to your physical device and select **B2** to route to OBS Mic/Aux in the future. If it's a fresh install it should have A1 and B1 selected for you already. Make sure to deselect B1. 

##### Setup Hardware Audio Output
Next lets setup your **hardware output** just to test for now. Select **A1** under hardware out and select your device of choice to test. Lets say your headphones! 

Whao! You should be able to hear yourself! and your desktop audio! You should also be able to see the bars move up and down. 

If not, lets check if we have things correct since I'm bad at writing guides. Here's a picture of what VMB should look like. 

![alt text](https://github.com/confusedbread/VoiceMeterSetup/blob/master/first%20settings.PNG "Logo Title Text 2")

Alright, we don't actually want feedback so lets deselect **A1** from **Hardware Input 1**.  

##### Fooling Around
*Optional--If you want to play around with the channel to get familiar lets have speakers on **A2** and select **A2** in **Hardware Input 1**. Your microphone should be playing through your speaker now! Be careful of feedback! Likewise you can channel microphone to your headphones and have desktop audio to your speakers if you put **A1** for **Hardware Input 1** and **A2** for **Hardware Input 2***. 


## Discord Integration 

You want to control when discord is on stream and balance the discord volume separate from the the output volume. Let's put that **virtual CABLE** you installed earlier to use.

#### On the Discord Side
So in Discord's Voice and Video Settings set the following. 
```
	Input Device -> VoiceMeeter Aux Output (VB-Audio VoiceMeeter AUX AVIO)
	Output Device -> CABLE Input (VB-Audio Virtual Cable)
```

#### On the VMB Side
Let's assign Discord to its own channel. In the **Hardware Input 2** channel Select **Cable Output (VB-Audio Virtual Cable**. Lets select **A1** to send audio to your physical device and **deselect** **B1** to avoid routing to OBS desktop in the future. You can reselect to your liking based on your streaming needs. 

## OBS Integration
Lets get this VMB integrated with OBS so we can stream already. Open OBS and go to **File --> Settings --> Audio**. Since you are using VMB for you audio you do **not** want to have desktop audio going to OBS directly. You instead need the VMB output. So make sure you **Disable** Desktop Audio by selecting **Disabled** for Desktop Audio. To bring you VMB desktop audio select the first **Mic/Auxiliary Audio** and select **VoiceMeeter Output (VB-Audio VoiceMeeter VAIO)**. For your microphone select **Mic/Auxiliary Audio 2** and select **VoiceMeeter Aux Output (VB-Audio VoiceMeter AUX VAIO)**. 

Here's a picture below on how it should look after. 

![alt text](https://github.com/confusedbread/VoiceMeterSetup/blob/master/Obs%20Audio.PNG "Logo Title Text z")



## Final Remarks and Concerns

CONGRATS! You should have VMB setup with control over discord audio going to OBS! 

### Wait a second I have lots of desktop audio vs mic audio lag!
Oh no! We messed up a configuration somewhere. :( But it's okay. To be more specific on the issue it's when your microphone audio is behind you OBS desktop audio (in the case of karaoke, hi chai). A likely reason for this issue is that OBS is receiving direct Desktop Output and not the VMB processed Desktop Output that you are hearing and singing to. Make sure you are not using **Desktop Audio** in OBS and using a **Mic/Auciliary Audio** to receive the VMB processed Desktop Output **VoiceMeeter Output (VB-Audio VoiceMeeter VAIO)**. 

#### It's still doesn't work :'(
I'm sorry if it all still doesn't work after all of this. Everyone's system or setup is different and it's hard to give a sure fix for your specific problem. You can reach back out to me to take a look if you're okay with that.

#### I want to be fancy and have audio playback for singing.
Whao there! You must be pretty good then to be thinking of music production. Unfortunately my answer to you is... Don't use voicemeter :( . With the virtual cable firmware the latency is a little too high for precise music production. Though if you are hell bent on using it follow the guide of this video to minimize latency https://www.youtube.com/watch?v=LAYKcIC5iFY&feature=youtu.be . 

#### I play rhythm games.....
I have some bad news. VMB will cause some latency when it comes to processing audio and piping it out to your headphones vs what you see on screen. It's between 100-300 ms probably default? unsure of the exact numbers but it'll ruin your experience. Again if you hell bent on using VMB refer to section above this one about audio playback. 