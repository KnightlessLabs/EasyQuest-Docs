# Handling Quest
Here I'll describe the methods you should use to properly handle quest. I won't go into implementation too much as that varies case
by case.

## _1. Accepting Quest_
To accept a quest, call `EasyQuestManager.Current.AcceptQuest(QuestID);`    
With QuestID being the ID of the quest you want to be in the player's quest list. This quest will now be tracked, and it's objectives can be updated as shown below.

## _2. Checking & Updating Quest Objective Info_

### General
There's a few useful methods to help check the progression of quest and objectives.     

For example, you can call `CheckQuestPrerequisitesCompleted(QuestID);` to see if the required quest(s) before the one being checked are done, which is useful, for example, for quest givers showing their quest status above their head.     

There's also `CheckIfTalkObjInProgress(QuestID, ConversationName);` that returns true if a talk objective is in progress for that quest, which is useful if you want the quest giver to talk to the player before actually finishing the quest.

### Go To/Move Object Objectives
These are handled by EasyQuestManager's "CheckQuestData" function. This is called during either FixedUpdate automatically
or manually whenever you want it to (explained in [EasyQuestManager Reference](EasyQuestManagerReference.md)) Note that **Go to** objectives need the player variable to be set as stated in the [Setup](./Setup.md) section.

Also note that for **Move Obj** quest, you want to pass a reference to the object by calling    
```   
EasyQuestManager.Current.SetQuestObjectReference(GameObject object, string ObjectName, bool Overwrite);
```  

The ObjectName is the one you set in the objective, so make sure those match. Overwrite is if you want to overwrite a reference
if it already has one. I recommend calling this in either the object's Start(); or OnEnable(); method.

### Collect/Defeat Objectives
For **Collect/Defeat** objectives, whenever an object is collected call the method `EasyQuestManager.Current.UpdateCollectObjectives(ItemName);`
or `EasyQuestManager.Current.UpdateEnemyObjectives(EnemyName);`, with ItemName/EnemyName being the name you decided for the objective.

### Return/Talk To Objectives
For **Return To/Talk To** objectives, call either `EasyQuestManager.Current.UpdateReturnObjectives(QuestID, ReturnerName);` or `EasyQuestManager.Current.UpdateTalkToObjectives(ConversationName);`.      
ReturnerName and ConversationName are the names you decided for the objective.

## 3. Updating Quest Log
`EasyQuestManager.Current.SetCurrentQuest(Index);` is useful if you want to show a quest to the player as their "Current Quest," however this can be ignored if you have your own implementation.

## 4. Finishing Quest
Quest are usually finished automatically, however if you unchecked "Auto-Complete Quest" then you can complete them manually by calling `EasyQuestManager.Current.QuestFinish(QuestID);`

## 5. What's Next
Besides this, there are some few useful event functions, which I describe in [EasyQuestManager Reference](EasyQuestManagerReference.md).
