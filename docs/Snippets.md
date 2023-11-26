### Snippets

This file describes the Snippets available with the extension, and the corresponding codes that will be generated.

### Usage

### `meth`

Generate Method

```Apex
${1|private,public,global|} ${2:returntype} {3:methodName} ${4}) {
    ${5}
}
```

### `smeth`

Generate Static Method

```Apex
${1|private,public,global|} static ${2:returntype} ${3:methodName}(${4}) {
      ${5}
}
```

### `aesmeth`

Generate AuraEnabled Static Method

```Apex
@AuraEnabled
${1|private,public,global|} static ${2:returntype} ${3:methodName}(${4}) {
      ${5}
}
```

### `aecsmeth`

Generate AuraEnabled Static Method with Cacheable=true

```Apex
@AuraEnabled(cacheable=true)
${1|private,public,global|} static ${2:returntype} ${3:methodName}(${4}) {
      ${5}
}
```

### `bclws`

Generate Batch Class with sharing boiler-plate code

```Apex
${1|private,public,global|} with sharing class ${2:${TM_FILENAME_BASE}} implements Database.Batchable<SObject> {

      // Class members
      ${3}

      // Class constructor
      ${4|private,public,global|} ${TM_FILENAME_BASE}(${5}) {
      		${6}
      }

      // Batch start
      ${7|private,public,global|} Database.QueryLocator start(Database.BatchableContext ${8:BC}) {
      \t${9}
      		String ${10:query} = ${11}
      		return Database.getQueryLocator(${10:query})
      }

      // Batch Execute
      ${12|private,public,global|} void execute(Database.BatchableContext ${8:BC}, ${13}) {
      		${14}
      }

      // Batch finish
      ${13|private,public,global|} void finish(Database.BatchableContext ${8:BC}) {
      		${14}
      }
}
```

### `sbclws`

Generate Stateful Batch Class with sharing boiler-plate code

```Apex
${1|private,public,global|} with sharing class ${2:${TM_FILENAME_BASE}} implements Database.Batchable<SObject>, Database.Stateful {

      // Class members
      ${3}

      // Class constructor
      ${4|private,public,global|} ${TM_FILENAME_BASE}(${5}) {
      		${6}
      }

      // Batch start
      ${7|private,public,global|} Database.QueryLocator start(Database.BatchableContext ${8:BC}) {
      		${9}
      		String ${10:query} = ${11}
      		return Database.getQueryLocator(${10:query})
      }

      // Batch Execute
      ${12|private,public,global|} void execute(Database.BatchableContext ${8:BC}, ${13}) {
      		${14}
      }

      // Batch finish
      ${13|private,public,global|} void finish(Database.BatchableContext ${8:BC}) {
      		${14}
      }
}
```

### `sclws`

Generate Schedulable Class with sharing boiler-plate code

```Apex
${1|private,public,global|} with sharing class ${2:${TM_FILENAME_BASE}} implements implements Schedulable {

      // Class members
      ${3}

      // Class constructor
      ${4|private,public,global|} ${TM_FILENAME_BASE}(${5}) {
      		${6}
      }

      // Execute method
      ${7|private,public,global|} void execute(SchedulableContext ${8:sc}) {
      		${9}
      }
}
```

### `soql`

SOQL String

```
[SELECT ${2:fieldnames} FROM ${1:objectname}];
```

### `soqlw`

SOQL String with WHERE clause

```
[SELECT ${2:fieldnames} FROM ${1:objectname} WHERE ${3:conditions}];
```

### `dbsr`

Database SaveResult boiler-plate code

```Apex
Database.SaveResult[] ${1:srList} = Database.${2|insert,update|}(${3}, ${4:false});

// Iterate through each returned result
for (Database.SaveResult ${5:sr} : ${1:srList}) {
      	if (${5:sr}.isSuccess()) {
      		${6}
      	} else {
          	// Get errors of failed operations
          	for(Database.Error ${7:err} : ${5:sr}.getErrors()) {
          		${8}
          	}
    }
}
```

### `dbur`

Database UpsertResult boiler-plate code

```
Database.UpsertResult[] ${1:urList} = Database.upsert(${2}, ${3:externalId}, ${4:false});

// Iterate through each returned result
for (Database.UpsertResult ${5:ur} : ${1:urList}) {
    if (${5:ur}.isSuccess()) {
      		${6}
    } else {
        	// Get errors of failed operations
          	for(Database.Error ${7:err} : ${5:ur}.getErrors()) {
         		${8}
          	}
    }
}
```

### `dbdr`

Database DeleteResult boiler-plate code

```
Database.DeleteResult[] ${1:drList} = Database.delete(${2}, ${3:false});

// Iterate through each returned result
for (Database.DeleteResult ${4:dr} : ${1:drList}) {
    if (${4:dr}.isSuccess()) {
        ${5}
    } else {
        // Get errors of failed operations
        for(Database.Error ${6:err} : ${4:dr}.getErrors()) {
            ${7}
        }
    }
}
```

### `dbudr`

Database UndeleteResult boiler-plate code

```Apex
Database.UndeleteResult[] ${1:udrList} = Database.undelete(${2}, ${3:false});

// Iterate through each returned result
for (Database.UndeleteResult ${4:udr} : ${1:udrList}) {
    if (${4:udr}.isSuccess()) {
        ${5}
    } else {
        // Get errors of failed operations
        for(Database.Error ${6:err} : ${4:udr}.getErrors()) {
            ${7}
        }
    }
}
```

### `dbiu`

Database Insert/Update

```
Database.SaveResult[] ${1:srList} = Database.${2|insert,update|}(${3}, ${4:false});
```

### `dbu`

Database Upsert

```
Database.UpsertResult[] ${1:urList} = Database.upsert(${2}, ${3:externalId}, ${4:false});
```

### `dbud`

Database Undelete

```
Database.UndeleteResult[] ${1:udrList} = Database.undelete(${2}, ${3:false});
```

### `dbd`

Database Delete

```
Database.DeleteResult[] ${1:drList} = Database.delete(${2}, ${3:false});
```

### `setm`

Single Email Text Message boiler-plate code

```Apex
// Define the mail
Messaging.SingleEmailMessage ${1:email} = new Messaging.SingleEmailMessage();

// Defining email params
String ${2:emailsubject} = ${3}
String ${4:emailbody} = ${4}
String ${5:emailaddresses} = new String[] {${6}}

// Setting email paramameters
${1:email}.setSubject(${2:emailsubject});
${1:email}.setPlainTextBody(${4:emailbody});
${1:email}.setToAddresses(${5:emailaddresses});

// Sending email
Messaging.SendEmailResult[] ${6:eres} = Messaging.sendEmail(new Messaging.SingleEmailMessage[]{${1:email}});
```

### `setma`

Single Email Text Message with Attachment boiler-plate code

```Apex
// Define the mail
Messaging.SingleEmailMessage ${1:email} = new Messaging.SingleEmailMessage();
// Define email attachment list
Messaging.EmailFileAttachment[] ${2:emailAttList} = new List<Messaging.EmailFileAttachment>();

// Defining attachment params
String ${3:attbodystr} = '${4}';
String ${5:attName} = '${6}';

// Create email attachment
Messaging.EmailFileAttachment ${7:efa} = new Messaging.EmailFileAttachment();
${7:efa}.setFilename(${5:attName});
${7:efa}.setBody(Blob.valueOf(${3:attbodystr}));
emailAttList.add(${7:efa});

// Defining email params
String ${8:emailsubject} = ${9}
String ${10:emailbody} = ${11}
String ${12:emailaddresses} = new String[] {${13}}

// Setting email paramameters
${1:email}.setSubject(${8:emailsubject});
${1:email}.setPlainTextBody(${10:emailbody});
${1:email}.setToAddresses(${12:emailaddresses});

// Sending email
Messaging.SendEmailResult[] ${13:eres} = Messaging.sendEmail(new Messaging.SingleEmailMessage[]{${1:email}});
```

### `ea`

Define email attachment

```Apex
// Create email attachment
Messaging.EmailFileAttachment ${1:efa} = new Messaging.EmailFileAttachment();
${2}
${1:efa}.setFilename(${3});
${1:efa}.setBody(${4});
emailAttList.add(${1:efa});
```

\-\-\-\-\-\- X ------
