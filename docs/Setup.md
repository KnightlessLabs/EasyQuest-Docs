
# EasyQuest Setup

## _1. Creating Manager_

### Automatic
Under **Tools/EasyQuest**, you can press **Create EasyQuest Manager** and it will handle the setup of the object for you. After this, make a new tag called "EQManager" and assign it to the object.

### Manually
Create an object and make sure it's tagged "EQManager", and attach both the **EasyQuestManager** and **QuestSaver** scripts to it.

On the EasyQuestManager, if it's not already assigned, make sure to assign the "Custom GUI Skin." It's in the root of the EasyQuest folder. Now you'll want to press the "Generate Quest Data" button, and you'll be setup the same as the automatic method.

## _2. Assigning the Player_
For certain quest you'll need to know the position of the player (currently for "GoTo" quest types). If you don't need this, you can skip this part.
 
You can assign the player's gameobject to the "Player" field on the EasyQuestManager directly, however this can also be assigned runtime like so:         
```
EasyQuestManager.Current.Player = playerObject;
```

## _3. Creating Quests_
That's it for setup, the next step is [Creating Quests](QuestManager/CreatingQuest.md)
