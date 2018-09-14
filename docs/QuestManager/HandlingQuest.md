# Handling Quest
Here I'll describe the methods you should use to properly handle quest. I won't go into implementation too much as that varies case
by case.

## 1. Accepting Quest
To accept a quest, call `EasyQuestManager.Current.AcceptQuest(QuestID);`    
With QuestID being the ID of the quest you want to be in the player's quest list. This quest will now be tracked.

## 2. Updating Quest Objective Info
This part depends on which objective your quest has. 

For **Go To/Move Obj** quest, this is handled by EasyQuestManager's "CheckQuestData" function. This is called during either FixedUpdate
or manually (explained in [EasyQuestManager Reference](EasyQuestManagerReference.md)) Note that **Go To** quest need the player variable to be set.
![]()

Note that for **Move Obj** quest, you want to pass a reference to the object by calling       
`EasyQuestManager.Current.SetQuestObjectReference(GameObject object, string ObjectName, bool Overwrite);`  

The ObjectName is the one you set in the objective, so make sure those match. Overwrite is if you want to overwrite a reference
if it already has one. I recommend calling this in either the object's Start(); or OnEnable(); method.

For **Collect/Defeat** quest, whenever an object is collected call the method `EasyQuestManager.Current.CheckCollectObj(ItemName);`
or `EasyQuestManager.Current.CheckEnemyObj(EnemyName);`, with ItemName/EnemyName being the name you decided for the objective.

For **Return To/Talk To** quest, call either `EasyQuestManager.Current.CheckReturnObj(QuestID, ReturnerName);` or `EasyQuestManager.Current.CheckTalkObj(ConversationName);`.      
ReturnerName and ConversationName are the names you decided for the objective.

## 3. Updating Quest Log
`EasyQuestManager.Current.SetCurrentQuest(Index);` is useful if you want to show a quest to the player as their "Current Quest," however this can be ignored if you have your own implementation.

## 4. Finishing Quest
Quest are usually finished automatically, however if you unchecked "Auto-Complete Quest" then you can complete them manually by calling `EasyQuestManager.Current.QuestFinish(QuestID);`

## 5. What's Next
Besides this, there are some few useful event functions, which I describe in [EasyQuestManager Reference](EasyQuestManagerReference.md).
