# EasyQuestManager Reference

There's a few useful events and methods that you can make use of.

## 1. Methods

### `void SaveQuestData();` and `void LoadQuestData();`
This saves/loads the Quest using the QuestSaver script. You might want to replace this method if you want all your save data in one file.

### `void SetCurrentQuest();`
This is useful if you want to show a quest to the player as their "Current Quest," however this can be ignored.

### `void CheckQuestData();`
If you have questCheckUpdate set to Manual, you will have to call this method yourself. This handles GoTo and MoveObj quest.


### `void AcceptQuest(int _QID)();`
Used to accept quest, adding them to the player's questlog.


### `void QuestFinish(int _QID);`
This is called automatically once a quest is finished unless "Auto Complete Quest" is set to false.


### `void SetQuestObjectReference (GameObject Object, string ObjectName, bool Overwrite);`
For any quest that needs to track an object's position, make sure this is called so that it has a reference to the object. Without this, the quest won't work.


### `bool CheckQuestPrerequisitesCompleted ( int QuestID);`
On the quest giver, you want to call this for all the quest they have to check if they're avaliable. The recommended usage is to call it after the **OnQuestGet** and **OnQuestFinish** events.


### `bool RequestTalkObjCompletionStatus( int QQID, string CN );`
For **Talk To** quest, use this when you need to know if the player should get a dialogue relating to the quest. Useful when you want a NPC to change it's dialogue depending on a quest being active.


### `void CheckReturnObj ( int QuestID, string ReturnerName );`
Call this when you want a return objective to be checked. The ReturnerName is what you defined in the objective itself.

### `void CheckTalkObj (string npcName);`, `void CheckCollectObj (string objName);`, 
### & `void CheckEnemyObj ( string enemyName );`
Called when you want one of these objectives to be checked.

## 2. Events

