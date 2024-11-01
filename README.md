# FA24-ReyesJ

# IMPORTANT!!
## Download the Cave Ruins, Medieval Dungeon, and Temperate Vegetation: Spruce Forest libraries from the Fab Library and import them into the project in order to run the game

## Youtube Videos

- [Homework 1 Video 1](https://youtu.be/5J2mlu4vlzc)
- [Homework 1 Video 2](https://youtu.be/AK34PJukp3I)

## How the Application works
### Plot, Targets, and Hazards
The game itself is a straightforward first person shooter, the player has been tasked with hunting monsters. However, the monsters do not fear the player, so the task of eliminating the targets is not as simple as just finding them. I used the monsters as both my target & hazard since both the player and monster can be eliminated by one another. _**I checked the rubric to be sure that it didn't specify we were not allowed to do this, if needed I can seperate the targets & hazards in HW2.**_

The player dies after being hit by the monsters 8 times while the monsters die after being shot 4 times, I initially set the monsters health to 5 hits but the difficulty when being swarmed made beating the levels too difficult. 

### Levels
- **Main Menu**: Sets the intiail tone of the game and introduces the monster (Viewable in the background at a distance). Using a Camera Actor viewpoint, I used the 'Set View Target with Blend' function to set a specific viewable area in the main menu level for the player. This allowed me to add detail to the main menu level that wouldv'e been impossible if I relied soley on the Main menu's UI blueprint alone. 
- **Level One**: Game setting is a forest that the player must traverse during a full moon, relying soley on their flashlight to see the monsters.
- **Level Two**: Game setting is deep within a cave that contains an underground ravine that homes a large nest of monsters. Player must traverse the ravine carefully or else they face falling into the ravine with not nearly enough ammo to eliminate the targets. 

### Pickups & Controls
- **Ammo**: The starting ammo and the ammount of ammo given by ammo pickups varies between the two levels based on the number of targets.
- **Health**: The health pickups have a set ammount of health they return for both levels. Players need to be careful to not pick them up when not needed since their health cannot exceed 100%.
- **Controls**: 
  - **Jump**: Default space bar key, only required in level two.
  - **Move**: Default W,A,S,D keys for moving forward, left, down, and right.
  - **Run**: Hold down shift while moving in any direction, required in both levels.
  - **Zoom**: Hold down caps-lock button, helps player see targets at a safer distance.
  - **Shooting**: Left-Click mouse or Single-click touchpad to shoot weapons' projectile.
  - **Flashlight**: Right-Click mouse or Double-click touchpad to turn on and off, required in both levels.

### Work Contributions 
I implemented all of the application and used many external resources to learn how to implement the extra features that I wanted my application to include. The rest of the README below details what the extra features are, what I used the features for, and the sources that taught me how to implement the features. I also included the fab library sources I used for their meshes.

## Extra Features & Source Citations

### Character & Animations: ~ Mixamo.com
- **Character**: Maynard
- **Animations**: Orc Idle, Walking, Running, Jump Attack
- **How these were used**:
  - Orc Idle, Walking, and Running were combined in an Animation Blueprint to give my monster a dynamic movement animation. Orc Idle is seen when the target is not moving, and walking is seen when the target is roaming its nav mesh boundary. Lastly, running occurs once the target has spotted the player and begins chasing them.
  - Jump Attack was used in a montage animation and played once the target has reached the player’s location to indicate the player has been hit.

### Sound Effects: ~ Pixabay.com
- **Sounds (Creator names in citation section)**:
  - Creaking door noise
  - Main Menu music
  - Running footsteps
  - “Psssttt” voice call
- **How these were used**:
  - The main menu music is the first sound heard when playing the game, so I used it to set the tone for what kind of game it is.
  - The second sound in the game is the creaking door noise. I timed this sound with a timeline function that pivots the door mesh.
  - The “Psst” sound effect is heard once the player has been spotted by the target (Through an AI perception component), it’s used to tell the player they are being hunted by the target; combining with a sound attenuation blueprint, I was able to get the sound effect to be spatialized when the player used headphones. This was useful since the game immerses the player in darkness (I included a flashlight feature with I/O to assist with this) and the targets could be in any direction of the player. This sound is implemented within the monster's behavior tree in the sequence for chasing the player.
  - The running footsteps sound effect is heard once the target begins chasing this player, it also uses a sound attenuation blueprint; however, I was not successful in HW 1 with implementing its spatialization. This sound is implemented within the running animation blueprint.

### Blackboard and Behavior Tree
- The Blackboard is a key/value storage component that has its variables shared across the behavior tree of my monster. The behavior tree has 2 separate sequences:
  - The first is the default behavior that allows the monster to roam its boundary box. I enjoyed implementing this because it made sure that players, including myself, could never predict where the enemy was on level one specifically.
  - The second activates once the player enters the line of sight of the monster (using an AI perception component), the player is then pursued and attacked until either the monster/player dies, or the player escapes the monster’s line of sight (seen at 2,000 cm and out of sight at 2,500 cm).

### AI Perception Component
- This component sits in the AI monsters controller blueprint and this is the prime feature that allows the monster to see the player, its settings allow for configuring how far the monster can spot the player as well as how wide its vision is on a half-angle scale.

### Flashlight Component
- This feature assists the player with visibility due to the lighting of my two levels, it’s implemented within the first-person character blueprint and it can be turned on and off by right-clicking with a mouse or double-clicking the touchpad.

### Level One’s Atmosphere
- I found an image taken by NASA of the moon and inserted it into a material blueprint, which was then applied to a sphere mesh to replicate a realistic moon in level one.

### Usage of ChatGPT
- I used AI to better stylize the lighting of my levels and RGB of certain components to give my levels a more horror-like feeling. Usage of AI can be seen in the following:
  - Flashlight’s Inner/Outer Scope setting & Attenuation setting
  - Sound Attenuation component settings
  - AI Perceptions’ half-angle setting
  - RGB for Ammo Pickup
  - RGB for weapon projectile
  - RGB for cave sunlight in level two

---

## Citations

I’d like to give a special thanks to the YouTuber [RubaDev](https://www.youtube.com/@RubaDev). Their content on creating a horror game in Unreal Engine provided me incredibly useful information which gave me a solid foundation for creating the idea I had for my horror game on HW1.

### Material Assistance
- [SVS Moon Image](https://www.lunarlamps.com/blogs/topic/photo-moon-lamp)
- [Emissive Materials](https://youtu.be/4b33FJ6yjuE?si=L0oRELXvWuwKj__r)
- [Learning How To Design Atmospheres](https://youtu.be/4b33FJ6yjuE?si=L0oRELXvWuwKj__r)

### AI Monster Component Assistance
- [Initial Monster AI Setup](https://youtu.be/k6GnKe5AM9k?si=9qH1nyjfTUjlnXZn)
- [Learning Behavior Tree & Blackboard](https://youtu.be/-t3PbGRazKg?si=StKIXAl-lGwy8HIS)
- [Additional Learning of Behavior Tree](https://youtu.be/VW8ZiV9yVDk?si=TOsf-YOxCTAzw4Vw)
- [AI Character Mesh & Animations](https://youtu.be/gsyZdKYAT_4?si=D1qhGov_S3vHk5Rt)
- [Learning AI Perception](https://youtu.be/mYRyx0OLUp4?si=J7PvDtiokXY2YtcH)

### Additional Assistance
- [Flashlight Component](https://youtu.be/N3lw_BgdKMo?si=R92MABJGwUjQE3zV)
- [Learning To Add Sound](https://youtu.be/woqUvTwgpDA?si=GOCrYmxHryKtuE03)
- [Main Menu Camera Usage](https://youtu.be/woqUvTwgpDA?si=GOCrYmxHryKtuE03)

### Websites
- Sound files: [Pixabay.com](https://pixabay.com/)
- Character Meshes & Animations: [Mixamo.com](https://www.mixamo.com/#/)

### Fab Library
- [Cave Ruins](https://fab.com/s/521e3b86e12d)
- [Medieval Dungeon](https://fab.com/s/494a7622e1be)
- [Temperate Vegetation: Spruce Forest](https://fab.com/s/de31b726d9df)

### Sound Creators on Pixabay
- **Creaking door noise**: u_ryiem47seu
- **Lost Souls (Main Menu music)**: SoundReality
- **Single footstep (Running sound)**: Pixabay
- **“Psssttt” voice call**: Ocean Eyes
