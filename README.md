## VE441 Team: FantasyAR

|                          Gradesheet                          |                          Team Info                           |                             Demo                             |                             Wiki                             |                            Trello                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| [<img src="https://eecs441.eecs.umich.edu/img/admin/grades3.png">][grade_sheet] | [<img src="https://eecs441.eecs.umich.edu/img/admin/team.png">][team_contract] | [<img src="https://eecs441.eecs.umich.edu/img/admin/video.png">][demo_page] | [<img src="https://eecs441.eecs.umich.edu/img/admin/wiki.png">][wiki_page] | [<img src="https://eecs441.eecs.umich.edu/img/admin/trello.png">][process_page] |


[grade_sheet]: https://docs.google.com/spreadsheets/d/1X3MaZ2m3UsdjcJARJQvdTjxElceTxeJx2uY92idq3xk/edit?usp=sharing
[team_contract]: https://docs.google.com/document/d/1YL6lX2RmaLtHDfeRCVXXIFOjAGVMu9O5j3gxOPFHA2Y/edit?usp=sharing
[demo_page]: https://www.youtube.com/watch?v=VIcOGEhsXGM&feature=youtu.be
[wiki_page]: https://github.com/eecs441staff/441template/wiki
[process_page]: https://trello.com/b/MyPhHMGd/441template



![cover](cover.png)

### Getting Started

#### List of front-end and back-end dependencies

| Name                | Link                                                         |
| ------------------- | ------------------------------------------------------------ |
| Unity AR Foundation | https://unity.com/unity/features/ar                          |
| GoMap               | https://assetstore.unity.com/packages/tools/integration/go-map-3d-map-for-ar-gaming-68889 |
| AR+GPS location     | https://assetstore.unity.com/packages/tools/integration/ar-gps-location-134882 |
| Recognissimo        | https://assetstore.unity.com/packages/tools/audio/recognissimo-cross-platform-offline-speech-recognition-203101 |
| Nginx               | https://www.nginx.com/                                       |
| Django              | https://www.djangoproject.com/                               |
| Gunicorn            | https://gunicorn.org/                                        |



### Model and Engine

#### Storymap

The following pictures shows our story map.

![story_map1](story_map1.png)

![story_map2](story_map2.png)

#### Block Diagram

The following picture is our engine architecture.

![Engine_Architecture](Engine_Architecture.jpg)

The front end provides the user location to the unity. With that information, unity can display the map and user avatar with the GO Map. Moreover, the front end provides the voice input, then Recognissimo will transfer it into a string in unity that acts as skill commands. The back end provides the enemy location to the unity, and with the scene captured by the phone's camera, AR+GPS location API will generate a game scene with the enemy in the real-time scene. And now the player is ready to play!

### APIs and Controller

We use Unity as our game engine. The front end will provide three pieces of information to the engine: user location, the scene captured by the camera, and the voice input. GO Map, AR+GPS location, and Recognissimo are downloaded from the unity asset store. They are packed perfectly and can communicate with the unity game engine automatically.

1. The first third-party API is GO Map. It can display the map in the real world based on user location, similar to Google Maps but with a game-style look. It will serve as a minimap that indicates to the player where the enemy or new missions are. The input for GO Map is the user location provided by GPS, the output is the minimap as well as the player avatar in the unity engine.
2. The second API is AR+GPS location. It can display AR models at specific locations as if the model is live in the scene captured by the camera. The input is the location of the monster in the real world, the output is to instantiate a monster model at that point in the unity engine.
3. The third API is Recognissimo, which is used for voice recognition. With the voice input by the user, it can convert the input into strings in unity. And then, skill commands in the game will be activated accordingly. The input is the user's voice, and the output is a string type to the unity engine.

The APIs used in the backend are shown below:

#### GetEnemyLocation

This function is to ensure that multiple players will see the same enemy in one location so that they can cooperate online.

**Request Parameters**

| Name           | Type    | Description                |
| -------------- | ------- | -------------------------- |
| PlayerLocation | Vector3 | The location of the player |

**Return Parameters**

| Name           | Type           | Description                             |
| -------------- | -------------- | --------------------------------------- |
| EnemyLocations | List<Vector3\> | The location of enemies near the player |
| EnemyTypes     | List<int\>     | The corresponding enemy type index      |



#### GetPlayerLevel

This function is used to get the player level that will be used for the scoreboard.

**Request Parameters**

| Name     | Type | Description             |
| -------- | ---- | ----------------------- |
| PlayerID | int  | Unique ID of the player |

**Return Parameters**

| Name  | Type | Description                     |
| ----- | ---- | ------------------------------- |
| Level | int  | The current level of the player |



#### GetPlayerSkill

This function is used to get the skills that the player has mastered.

**Request Parameters**

| Name     | Type | Description             |
| -------- | ---- | ----------------------- |
| PlayerID | int  | Unique ID of the player |

**Return Parameters**

| Name   | Type       | Description           |
| ------ | ---------- | --------------------- |
| Skills | List<int\> | A List of skill index |





### View UI/UX



### Team Roster

| Name           | Contribution |
| -------------- | ------------ |
| Qihan Ren      |              |
| Zesheng Yu     |              |
| Yanjun Chen    |              |
| Zhongqian Duan |              |
| Yangdong Huang |              |

