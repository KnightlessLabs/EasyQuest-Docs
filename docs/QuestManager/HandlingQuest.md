# Handling Quest
Here I'll describe the methods you should use to properly handle quest. I won't go into implementation too much as that varies case
by case.

## 1. Accepting Quest
To accept a quest, call     
`EasyQuestManager.Current.AcceptQuest(QuestID);`    
With QuestID being the ID of the quest you want to be in the player's quest list. This quest will now be tracked.

## 2. Updating Quest Objective Info
This part depends on which objective your quest has. 

For **Go To/Move Obj** quest, this is handled by EasyQuestManager's "CheckQuestData" function. This is called during either FixedUpdate
or manually as shown below. Note that **Go To** quest need the player variable to be set.
![]()

Note that for **Move Obj** quest, you want to pass a reference to the object by calling       
`EasyQuestManager.Current.SetQuestObjectReference(GameObject object, string ObjectName, bool Overwrite);`  

The ObjectName is the one you set in the objective, so make sure those match. Overwrite is if you want to overwrite a reference
if it already has one.

For **Collect/Defeat** quest, 
