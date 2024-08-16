# Food-Connect
A CRM Application to Supply Leftover Food to Poor


##Trigger Name: DropOffTrigger

Object: Drop_Off_point__c

Description:
This trigger is designed to ensure that the Distance__c field on the Drop_Off_point__c object is always synchronized with the distance_calculation__c field before a new record is inserted. 
This synchronization is crucial for maintaining accurate distance data, which can be used for setting up sharing rules and other distance-related logic.

Code:
```
apex
Copy code
trigger DropOffTrigger on Drop_Off_point__c (before insert) {

    for(Drop_Off_point__c Drop : Trigger.new){

        Drop.Distance__c = Drop.distance_calculation__c;

    }

}
```


* Functionality:
       * Trigger Event: Before Insert - This trigger executes before new Drop_Off_point__c records are saved to the database.

       * Logic: For each record in the Trigger.new collection (which contains the new Drop_Off_point__c records being inserted), the trigger sets the Distance__c 
                field to the value of the distance_calculation__c field.
       
       * Purpose: The primary purpose of this trigger is to ensure that the Distance__c field accurately reflects the distance calculated in the 
                   distance_calculation__c field. This alignment is necessary for utilizing
                   the distance data in sharing rules and other processes where the distance information is critical.

* Usage: This trigger is particularly useful in scenarios where sharing rules or other business logic depend on distance values. By ensuring that Distance__c 
                is populated correctly at the time of record creation,
                the trigger helps in maintaining data consistency and integrity.

