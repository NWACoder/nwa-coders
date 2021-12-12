# Notion
[Notion API](https://developers.notion.com/)
Setup an Internal integration 
[Integration](https://www.notion.so/my-integrations)
Setup Internal Integration Token in .env file NOTION_AUTH

Share Access to your internal integration
Create the following Tables in your Notion Workspace

## Meet UP Schedule

**Name**
Type: Title

**Day**
Type: Date

**Status**
Type: Select
* Draft
* Published
* Done

**Time**
Type: Text

**Type**
Type: Select
* Virtual
* in-Person
* Youtube
* Discord

**Speaker**
Type: Relation
Speaker

**Link**
Type: URL


## Guest Speakers

**Name**
Type: Title

**Slug**
Type: Text

**Topic**
Type: Text

**Date**
Type: Date

**Image**
Type: Text

**Status**
Type: Select
* Draft
* Published

**Role**
Type: Text

**Video**
Type: Text

**Email**
Type: Text

**Bio**
Type: Text

**Related to Meet UP Schedule (Speaker)**
Type: Relation
Meet UP Schedule