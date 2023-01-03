---
layout: post
title: "Vitreoretinal Surgical Medical Device"
date: 2021-05-05
categories: projects
featured_image: depressor.jpeg
excerpt_separator: <!--more-->
---
### Impetus

For my senior capstone project, I led a team of nine composed of physicians and engineers to create an integrated medical device to improve vitreoretinal surgery. Vitreoretinal surgery refers to a group of advanced, highly delicate procedures that are done deep inside the eye's interior near the retina. This group of surgeries requires the use of three instruments simultaneously:

- Vitrector (used for cutting, suction, and laser ablation)
- A light source
- Scleral depressor

All three of these instruments are handheld and this necessitates a second individual to assist the lead surgeon and hold one of the three. This results in longer surgeries, more incisions, and higher costs / risks.

![Diagram of Eye Surgery](/assets/images/eyeDiagram.png){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
Diagram of vitrector and light being used in surgery. Not pictured is the scleral depressor.

![Traditional Scleral Depressor](/assets/images/Olddepressor.jpeg){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
A traditional scleral depressor, used to push and manipulate the white outer wall of the eye (scleral wall). 

### Proposed Solution

Our team's solution is to combine the light source and scleral depressor into a single device. The direction of illumination can easily adjusted as surgery progresses and transillumination through scleral wall removes the need for a second individual for surgery. 

![CAD Render of Solution](/assets/images/depressor.jpeg){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
Rendering of our team's original design

### Funding Acquisition

Our team's initial budget was only $500 worth of materials. Due to the need for custom printed circuit boards, 3D printed metal prototypes, and wet lab costs this was a roadblock. I identified two grants that provided potential additional sources of funding. After leading our team through the multiple application rounds, we were awarded an additional $5,000. These additional funds allowed for much faster development timelines, and a higher quality final device.

### Key Parameters

There were three subsystems and corresponding design parameters that our team identified that would need to be refined as we progressed through the iterative design process. They were broken down as such:

- LED Lighting
  - Intensity Level
  - Emission Color
  - Angle of Projection
- Physical Housing
  - Material
  - Dexterity
  - Size / weight
- Safety
  - Photo toxicity
  - Heat
  - Disposable vs Reusable

### Iterative Prototype Development

We used biweekly sprints to structure our development process. We would begin the first week by identifying areas of potential improvement, break into our respective sub teams, and finalize the new design changes by Friday when we would place an order for the respective parts. Items would arrive by the following Wednesday, where they would then be assembled and verified. The next day we would pass the prototype off to the physicians, who would lead a testing in a wet lab at the Duke Eye Center in porcine (pig) eyes. These live tests would produce highly productive feedback that would be addressed in the following sprint. Overall, our team went through eleven full iterations. 

![11 Iterations](/assets/images/11models.png){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
The Mark I -> Mark XI


### Challenges / Solutions

There were dozens of minor changes that were implemented throughout the entire design process, but the three largest were:

- Problem: initial brightness was too low for real-world use
  - Solution: A larger number of higher voltage LEDs were placed closer to the surface
- Problem: Correctly positioning the classic LEDs in the head was intractable
  - Solution: We designed a custom printed board to enable surface mounting of flat LEDs
- Problem: Soldering near the battery pack was causing battery explosions
  - Solution: We designed a custom battery pack with a spring and copper tape to replace the soldering



![Detailed CAD Render of Solution](/assets/images/CADModel.jpeg){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
Design of the final prototype, the Mark XI is shown below.


![Detailed CAD Render of Solution](/assets/images/realDepressor.jpeg){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
Picture of the Mark XI with hand for scale

![Artificial Eye View](/assets/images/unlitEye.png){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}
![Artificial Eye View](/assets/images/litEye.png){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
Images of the Mark XI in front of an artificial eye (lit and unlit)

![Artificial Eye View](/assets/images/bloodVessel.jpg){:style="display:block; margin-left:auto; margin-right:auto; width: 700px; height: auto"}

{:.imageSubscript} 
The Mark XI viewed through a microscope as it transilluminates through a live porcine eye highlighting a retinal blood vessel. 

### End Result

With the Mark XI our team was able to achieve a medical device capable of 84 minutes of continual use (3x longer than the average surgery) and a cost per unit of $225. The device is designed to be a disposable single use device and complies with regulatory standards for thermal load and optical radiation within standard phototoxicity levels.

Duke's Office of License and Ventures has used my team's work to file for a provisional patent for an illuminated scleral depressor for vitreoretinal surgery. 
