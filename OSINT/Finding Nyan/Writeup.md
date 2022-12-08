# Stack The Flags 2022: Finding Nyan

![Contest Date: 02.12.2022](https://img.shields.io/badge/Contest%20Date-02.12.2022-lightgrey.svg)
![Solve Moment: During The Contest](https://img.shields.io/badge/Solve%20Moment-During%20The%20Contest-brightgreen.svg)
![Difficulty: Medium](https://img.shields.io/badge/Difficulty-Medium-orange)

## Description

> Jaga is on a road trip to find Nyan. Do you know which road is this in the meteverse?

> Note that for this challenge, the road name is case sensitive, example - `STF22{Jln_Binchang}`. The road name should be the exact address seen on Google Maps



## Attached Files

- Finding Nyan.MOV
- https://tinyurl.com/bdk5pwj6 (download link for video)

## Summary

We find a speed camera, as well as a Bukit Batok Driving Centre car. We then look through speed cameras in Bukit Batok and find the road.

## Flag

```
STF22{BUKIT_BATOK_RD}
```

## Detailed Solution

When we watch the video, we can see that the person is driving down a road, next to a construction site.\
If we slow down the video and watch it frame by frame, we discover that there is a **speed camera**
![1.png](1.png)\
Even though it looks similar to a red light camera, the camera is not near a traffic light, so it is a speed camera.
Speed cameras are useful when spotted, as there are lists of speed cameras in Singapore online and it can become easy to narrow down where the video is taken at.\
The one that we used for the challenge was ![this](https://data.gov.sg/dataset/location-of-speed-enforcement-cameras).

At the bottom of the list, it tells us that there are 91 speed cameras in Singapore as of 2019\
Even though we could look through all 91 locations, it would not only be boring, but also take a long time.

Instead, we looked through the video again and found that a car from **Bukit Batok Driving Centre** happened to drive along that road\
![2.png](2.png)\
Even though it was very blurry, we double checked it with ![their website](https://info.bbdc.sg/) and it was the same car.

Knowing this, we checked the list again and there were 2 speed cameras at Bukit Batok, one at **Bukit Batok Road** towards Chua Chu Kang Road, and another at **Bukit Batok Road** towards Jurong Town Hall Road. Both of them were at Bukit Batok road so it should be correct. Just to confirm, we checked google maps.

Indeed, we could see the speed camera and the construction site in the background.
![3.png](3.png)

```
STF22{BUKIT_BATOK_RD}
```
