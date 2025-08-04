 # Data Schema
General note :
1. `xxID` are not for display to users
2. `tenant` is not for display to users
3. `tenant`/`secClass`/`blacklist` is for the classification of the information



<details> <summary>Phase 1 tables</summary>

### `agency`

| Column Name     | Data Type                | Constraints  | show in UI & example                             |
| --------------- | ------------------------ | ------------ |--------------------------------------------------|
| agencyId        | uuid                     | PK, not null | No ...eg 1b5ff2b0-780e-4ac5-a97d-d5affb02451c    |
| agencyName      | text                     | nullable     | Feiyue Family Services, KCC Constituency Office   |
| agencyType      | text                     | nullable     | Govt, PA et
| block           | text                     | nullable     | 04, 04M
| floor           | text                     | nullable     | 1234A     
| street          | text                     | nullable     | Ang Mo Kio Ave 1
| postalcode      | text 6 chars             | nullable     | 323451
| buildingName    | text                     | nullable     | Cheng Ho Industrial Bldg
| agencyEmail     | text                     | nullable     | test@hotmail.com
| servicesOffered | ARRAY, text enum         | nullable     | see below
| hotline         | numeric 6 nums           | nullable     | 61234567
| remarks         | text                     | nullabalbe   | for comments abt agency
| multimedia      | ARRAY,UUID               | nullable     | 
| tenant          | text 3-5 chars           | nullable     | No - tpyn, chpg 
| secClass        | ARRAY,text enum,         | nullable     | see below
| blacklist       | ARRAY,UUID               | nullable     | `user.userID`
| updatedAt       | timestamp  now()         | nullable     | No
| updatedBy       | uuid                     | nullable     | No - `user.userID`

`servicesOffered` array includes Counselling, Financial Aid, Food Delivery, Home Services, Home Visits, etc
`secClass` array includes VVIP, Sexual, Violence, Foreign, Police, Criminal

## `agency_engagements`

| Column Name         | Data Type                | Constraints  |show in UI & example                             |
| ------------------- | ------------------------ | ------------ |-------------------------------------------------|
| agencyEngagementsID | uuid                     | PK, not null | No
| agencyID            | uuid                     | nullable     | No
| engagementType      | ARRAY,text enum          | nullable     | see below
| caseOfficerID       | uuid                     | nullable     |
| engagementDetails   | text                     | nullable     |
| householdID         | ARRAY,uuid               | nullable     | 
| residentID          | ARRAY,uuid               | nullable     |
| startDate           | date                     | nullable     |
| endDate             | date                     | nullable     | 
| multimedia          | ARRAY,uuid               | nullable     |
| tenant              | text                     | nullable     | No
| secClass            | ARRAY                    | nullable     | No
| blacklist           | ARRAY,uuid               | nullable     | No
| updatedAt           | timestamp  now()         | nullable     | No
| updatedBy           | uuid                     | nullable     | No

`engagementType` array includes Counselling, Financial Aid, Food Delivery, Home Services, Home Visits etc

## `case`

| Column Name     | Data Type                | Constraints  |show in UI & example                             |
| --------------- | ------------------------ | ------------ |-------------------------------------------------|
| caseID          | uuid                     | PK, not null | No
| caseTitle       | text                     | nullable     |
| caseSummary     | text                     | nullable     |
| caseDetails     | text                     | nullable     |
| agencyID        | uuid                     | nullable     |
| caseOfficerID   | uuid                     | nullable     |
| staffInChargeID | uuid                     | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| tenant          | text                     | nullable     | No
| secClass        | ARRAY                    | nullable     | No
| blacklist       | ARRAY,UUID               | nullable     | No
| updatedAt       | timestamp now()          | nullable     | No
| updatedBy       | uuid                     | nullable     | No


## `case_involvements`

| Column Name        | Data Type                | Constraints  |show in UI & example                             |
| ------------------ | ------------------------ | ------------ |-------------------------------------------------|
| caseInvolvementsID | uuid                     | PK, not null | No
| caseID             | uuid                     | nullable     | No
| householdID         | ARRAY                    | nullable     | either household or both
| residentID          | ARRAY                    | nullable     | but not for both. One for each.
| caseRole           | ARRAY,text enum          | nullable     | eg Victim, Complainant, Onlooker, Witness
| description        | text                     | nullable     |
| multimedia         | ARRAY,UUID               | nullable     |
| tenant             | text                     | nullable     | No
| secClass           | ARRAY                    | nullable     | No
| blacklist          | ARRAY,UUID               | nullable     | No
| updatedAt          | timestamp with time zone | nullable     | No
| updatedBy          | uuid                     | nullable     | No

## `case_statuses`

| Column Name    | Data Type                | Constraints  |show in UI & example                             |
| -------------- | ------------------------ | ------------ |-------------------------------------------------|
| caseStatusesID | uuid                     | PK, not null | No
| caseID         | uuid                     | nullable     |
| caseStatus     | text                     | nullable     |
| reasonStatus   | text                     | nullable     |
| statusDate     | date                     | nullable     |
| multimedia     | ARRAY,UUID               | nullable     |
| tenant         | text                     | nullable     | No
| secClass       | ARRAY                    | nullable     | No
| blacklist      | ARRAY,UUID               | nullable     | No
| updatedAt      | timestamp with time zone | nullable     | No
| updatedBy      | uuid                     | nullable     | No


## `event`

| Column Name      | Data Type                | Constraints  |show in UI & example                             |
| ---------------- | ------------------------ | ------------ |-------------------------------------------------|
| eventID          | uuid                     | PK, not null | No
| eventTitle       | text                     | nullable     |
| eventDescription | text                     | nullable     | 
| eventLocation    | text   
| eventGeopoint    | text                     | nullable     |
| eventPosterUrl   | text                     | nullable     |
| maxVolunteers    | number                   | nullable     | yes
| staffInChargeID  | uuid                     | nullable     |
| agencyID         | uuid                     | nullable     |
| g_conferenceData | ARRAY jsonb
| g_creator        | jsonb
| g_start          | jsonb                    | nullable     |
| g_end            | jsonb                    | nullable     |
| g_eventType      | text
| g_extendedProperties| jsonb
| g_iCalUID        | text
| g__id            | text
| g_kind           | text
| g_organizer      | jsonb
| g_privateCopy    | boolean
| g_reminders      | ARRAY jsonb
| g_sequence       | int
| g_status         | text
| g_updated        | datetime
| multimedia       | ARRAY,UUID               | nullable     |
| tenant           | text                     | not null     | No
| secClass         | ARRAY                    | nullable     | No
| blacklist        | ARRAY,UUID               | nullable     | No
| updatedAt        | timestamp                | not null     | No
| updatedBy        | uuid                     | nullable     | No

google calendar api https://developers.google.com/workspace/calendar/api/v3/reference/events
`g_attendees` incudes 
additionGuests int
comment text
displayName text
email text
id text
option boolean
organizer boolean
resource boolean
responseStatus text
self boolean

`conferenceData` includes
conferenceID text
conferenceSolution jsonb
conferenceSolution.iconUri text
conferenceSolution.key jsonb



## `event_activities`

| Column Name         | Data Type                | Constraints  |show in UI & example                             |
| ------------------- | ------------------------ | ------------ |-------------------------------------------------|
| eventActivitiesID   | uuid                     | PK, not null | No
| eventID             | uuid                     | nullable     | No
| activityType        | ARRAY                    | nullable     |
| activityDescription | text                     | nullable     |
| householdID         | ARRAY                    | nullable     | either household or both
| residentID          | ARRAY                    | nullable     | but not for both. One for each.
| multimedia          | ARRAY,UUID               | nullable     |
| tenant              | text                     | nullable     | No
| secClass            | ARRAY                    | nullable     | No
| blacklist           | ARRAY,UUID               | nullable     | No
| updatedAt           | timestamp with time zone | nullable     | No
| updatedBy           | uuid                     | nullable     | No

## `event_requirements`

| Column Name         | Data Type                | Constraints  |show in UI & example                             |
| ------------------- | ------------------------ | ------------ |-------------------------------------------------|
| eventRequirementsID | uuid                     | PK, not null | No
| eventID             | uuid                     | not null     | No
| eventRequirement    | text                     | nullable     |
| startTime           | timestamp                | nullable     |
| endTime             | timestamp                | nullable     |
| requirementLocation | text                     | nullable     |
| meetingLocation     | text                     | nullable     |
| meetingTime         | timestamp                | nullable     |
| "usersInvolved"     | link to `staff_contributions table 
| externalVolunteers  | ARRAY                    | nullable     |
| multimedia          | ARRAY,UUID               | nullable     |
| maxVolunteers       | number                   | nullable     |  
| tenant              | text                     | nullable     | No
| secClass            | ARRAY                    | nullable     | No
| blacklist           | ARRAY,UUID               | nullable     | No
| updatedAt           | timestamp                | not null     | No
| updatedBy           | uuid                     | nullable     | No

## `household`

| Column Name    | Data Type                | Constraints  |show in UI & example                             |
| -------------- | ------------------------ | ------------ |-------------------------------------------------|
| householdID    | uuid                     | PK, not null | No
| block          | text                     | nullable     | eg 103A
| floor          | text                     | nullable     | eg 04, 04M
| unit           | text                     | nullable     | eg 1234A
| street         | text                     | nullable     | eg Ang Mo Kio Ave 1
| postalcode     | character varying        | nullable     | eg 323451
| unitName       | text                     | nullable     | eg Cheng Huat Metals
| entrance       | text                     | nullable     | eg Lift Lobby A
| buildingName   | text                     | nullable     | eg Cheng Ho Industrial Bldg
| estateName     | text                     | nullable     | eg Ho Bee Estate
| houseType      | text enum                | nullable     | eg HDB5Rm, EC, Condominium,Terrace,Semi-D,Bungalow 
| rn             | text                     | nullable     | eg Garden Vale
| constituency   | text                     | nullable     | eg Kampong Chai Chee
| race           | text                     | nullable     |
| religion       | text                     | nullable     |
| houseOwnership | text                     | nullable     | eg Rental, Owned
| spokenLanguage | ARRAY                    | nullable     | Chinese, Malay, Tamil, English, Teochew, Cantonese
| incomeLevel    | text                     | nullable     | High Income, Mid Income, Low Income, No Income
| email          | text                     | nullable     |
| mobile         | numeric                  | nullable     |
| homePhone      | numeric                  | nullable     |
| personality    | ARRAY                    | nullable     | Friendly, Aggressive, Outgoing 
| remarks        | text                     | nullable     |
| multimedia     | ARRAY,UUID               | nullable     |
| tenant         | text                     | nullable     | No
| secClass       | ARRAY                    | nullable     | No
| blacklist      | ARRAY,UUID               | nullable     | No
| updatedAt      | timestamp with time zone | nullable     | No
| updatedBy      | uuid                     | nullable     | No

## `household_occupants`

| Column Name  | Data Type                | Constraints  |show in UI & example                             |
| ------------ | ------------------------ | ------------ |-------------------------------------------------|
| occupantID   | uuid                     | PK, not null | No
| householdID  | uuid                     | not null     |
| residentID   | uuid                     | not null     |
| familyRole   | text                     | nullable     |
| stillStaying | boolean                  | nullable     |
| multimedia   | ARRAY,,UUID              | nullable     |
| tenant       | text                     | nullable     | No
| secClass     | ARRAY                    | nullable     | No
| blacklist    | ARRAY,UUID               | nullable     | No
| updatedAt    | timestamp with time zone | nullable     | No
| updatedBy    | uuid                     | nullable     | No


## `household_support`

| Column Name     | Data Type                | Constraints  |show in UI & example                             |
| --------------- | ------------------------ | ------------ |-------------------------------------------------|
| householdID      | uuid                     | PK, not null | No
| supportParty    | boolean                  | nullable     |
| supportAdvisor  | boolean                  | nullable     |
| advisor         | text                     | nullable     |
| additionalInfo  | text                     | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| tenant          | text                     | nullable     | No
| secClass        | ARRAY                    | nullable     | No
| blacklist       | ARRAY,UUID               | nullable     | No
| updatedAt       | timestamp with time zone | nullable     | No
| updatedBy       | uuid                     | nullable     | No


## `logs` - not to shown in UI

| Column Name  | Data Type                | Constraints  |show in UI & example                             |
| ------------ | ------------------------ | ------------ |-------------------------------------------------|
| logsID       | uuid                     | PK, not null | No
| action       | text                     | nullable     | No
| tableUpdated | text                     | nullable     | No
| fieldUpdated | text                     | nullable     | No
| oldValue     | text                     | nullable     | No
| newValue     | text                     | nullable     | No
| tenant       | text                     | nullable     | No
| secClass     | ARRAY                    | nullable     | No
| blacklist    | ARRAY,UUID               | nullable     | No
| updatedAt    | timestamp with time zone | nullable     | No
| updatedBy    | uuid                     | nullable     | No

## `multimedia`

| Column Name      | Data Type                | Constraints  |show in UI & example                             |
| ---------------- | ------------------------ | ------------ |-------------------------------------------------|
| multimediaID     | uuid                     | PK, not null | No
| mediaUrl         | text                     | nullable     |
| mediaType        | text                     | nullable     |
| mediaTitle       | text                     | nullable     |
| mediaDescription | text                     | nullable     |
| tenant           | text                     | nullable     | No
| secClass         | ARRAY                    | nullable     | No
| blacklist        | ARRAY,UUID               | nullable     | No
| updatedAt        | timestamp with time zone | nullable     | No
| updatedBy        | uuid                     | nullable     | No

## `resident`

| Column Name     | Data Type                | Constraints  |show in UI & example                             |
| --------------- | ------------------------ | ------------ |-------------------------------------------------|
| residentID      | uuid                     | PK, not null | No
| preferredName   | text                     | nullable     |
| officialName    | text *encrypted          | nullable     |
| officialID      | text *encrypted          | nullable     |
| typeID          | text                     | nullable     |
| profilePicUrl   | text                     | nullable     |
| description     | text                     | nullable     |
| race            | text                     | nullable     |
| educationLevel  | text                     | nullable     |
| gender          | text                     | nullable     |
| spoken_language | ARRAY                    | nullable     |
| religion        | text                     | nullable     |
| email           | text                     | nullable     |
| mobile          | numeric                  | nullable     |
| occupation      | text                     | nullable     |
| employer        | text                     | nullable     |
| employmentType  | text                     | nullable     |
| verbalAddress   | text                     | nullable     |
| personality     | ARRAY                    | nullable     |
| remarks         | text                     | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| tenant          | text                     | nullable     | No
| secClass        | ARRAY                    | nullable     | No
| blacklist       | ARRAY,UUID               | nullable     | No
| updatedAt       | timestamp with time zone | nullable     | No
| updatedBy       | uuid                     | nullable     | No

## `resident_support`

| Column Name     | Data Type                | Constraints  |show in UI & example                             |
| --------------- | ------------------------ | ------------ |-------------------------------------------------|
| residentID      | uuid                     | PK, not null | No
| supportParty    | boolean                  | nullable     |
| supportAdvisor  | boolean                  | nullable     |
| advisor         | text                     | nullable     |
| additionalInfo  | text                     | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| tenant          | text                     | nullable     | No
| secClass        | ARRAY                    | nullable     | No
| blacklist       | ARRAY,UUID               | nullable     | No
| updatedAt       | timestamp with time zone | nullable     | No
| updatedBy       | uuid                     | nullable     | No


## `task`

| Column Name   | Data Type                | Constraints  |show in UI & example                             |
| ------------- | ------------------------ | ------------ |-------------------------------------------------|
| taskID        | uuid                     | PK, not null | No
| caseID        | uuid                     | nullable     | 
| task          | text                     | nullable     |
| agencyID      | uuid                     | nullable     |
| taskOfficerID | uuid                     | nullable     |
| officerMobile | numeric                  | nullable     |
| multimedia    | ARRAY,UUID               | nullable     |
| tenant        | text                     | nullable     | No
| secClass      | ARRAY                    | nullable     | No
| blacklist     | ARRAY,UUID               | nullable     | No
| updatedAt     | timestamp with time zone | not null     | No
| updatedBy     | uuid                     | nullable     | No


## `task_status`

| Column Name    | Data Type                | Constraints  |show in UI & example                             |
| -------------- | ------------------------ | ------------ |-------------------------------------------------|
| taskStatusesID | uuid                     | PK, not null | No
| taskID         | uuid                     | not null     | No
| taskStatus     | text                     | nullable     |
| statusReason   | text                     | nullable     |
| statusDate     | date                     | nullable     |
| multimedia     | ARRAY,UUID               | nullable     |
| tenant         | text                     | nullable     | No
| secClass       | ARRAY                    | nullable     | No
| blacklist      | ARRAY,UUID               | nullable     | No
| updatedAt      | timestamp with time zone | nullable     | No
| updatedBy      | uuid                     | nullable     | No

## `user`

| Column Name    | Data Type                | Constraints  |show in UI & example                             |
| -------------- | ------------------------ | ------------ |-------------------------------------------------|
| userID         | uuid                     | PK, not null | No
| agencyID       | uuid                     | nullable     |
| roleAgency     | text,enum                | nullable     | eg Volunteer, Staff, Admin, Advisor
| staffType      | text,enum                | nullable     | eg Perm Volunteer, Temp volunteer, Adhoc Helper
| verbalName     | text                     | nullable     |
| officialName   | text  *encrypted         | nullable     |
| officialID     | text  *encrypted         | nullable     |
| gender         | text                     | nullable     |
| idType         | text                     | nullable     |
| profilePicUrl  | text                     | nullable     |
| description    | text                     | nullable     |
| race           | text                     | nullable     |
| educationLevel | text                     | nullable     |
| personality    | ARRAY                    | nullable     |
| spokenLanguage | ARRAY                    | nullable     |
| religion       | text                     | nullable     |
| occupation     | text                     | nullable     |
| employer       | text                     | nullable     |
| employmentType | text                     | nullable     |
| email          | text                     | nullable     |
| mobile         | numeric                  | nullable     |
| multimedia     | ARRAY,UUID               | nullable     |
| tenant         | text                     | nullable     | No
| secClass       | ARRAY                    | nullable     | No
| blacklist      | ARRAY,UUID               | nullable     | No
| updatedAt      | timestamp with time zone | nullable     | No
| updatedBy      | uuid                     | nullable     | No

## `staff_contributions`

| Column Name        | Data Type                | Constraints  |show in UI & example                             |
| ------------------ | ------------------------ | ------------ |-------------------------------------------------|
| staffContributionsID| uuid                     | PK not null  | No
| userID             | uuid                     | nullable     | No
| entityType         | text                     | nullable     | eg agency_engagement, event, event_requirements, event_activities, task,
| entityID           | uuid                     | nullable     | uuid of the above relevant module
| role               | ARRAY,text enum          | nullable     | eg participant, action party, role in event
| description        | text                     | nullable     |
| status             | text                     | nullable     | eg status in attending event
| multimedia         | ARRAY,UUID               | nullable     |
| tenant             | text                     | nullable     | No
| secClass           | ARRAY                    | nullable     | No
| blacklist          | ARRAY,UUID               | nullable     | No
| updatedAt          | timestamp with time zone | nullable     | No
| updatedBy          | uuid                     | nullable     | No


## `notification`

| Column Name        | Data Type                | Constraints  |show in UI & example                             |
| ------------------ | ------------------------ | ------------ |-------------------------------------------------|
| notificationID     | uuid                     | PK not null  | No
| userID             | uuid                     | nullable     | No
| notificationType   | text                     | nullable     | eg agency_engagement, event, event_requirements, event_activities, task,
| notification       | text                     | nullable     | description of the notification
| picUrl             | text                     | nullable     |    
| creationDate       | timestamp                | nullable     |
| isRead             | boolean                  | nullable     | eg status in attending event
| multimedia         | ARRAY,UUID               | nullable     |
| tenant             | text                     | nullable     | No
| secClass           | ARRAY                    | nullable     | No
| blacklist          | ARRAY,UUID               | nullable     | No
| updatedAt          | timestamp with time zone | nullable     | No
| updatedBy          | uuid                     | nullable     | No


## `error` - not in UI

| Column Name   | Data Type                | Constraints  |show in UI & example                             |
| ------------- | ------------------------ | ------------ |-------------------------------------------------|
| errorID       | uuid                     | PK, not null | No
| module        | text                     | nullable     | No
| field         | text                     | nullable     | No
| situation     | text                     | nullable     | No
| errorMessage  | text                     | nullable     | No
| userInvolved  | uuid                     | nullable     | No
| datetimeError | timestamp with time zone | nullable     | No



# Views `credentials`
| Column Name   | Data Type                | Constraints  |show in UI & example                             |
| ------------- | ------------------------ | ------------ |-------------------------------------------------|
| userID        | uuid                     | PK, not null | No
| authorised    | boolean                  | nullable     | 
| tenant        | text                     | nullable     | No

</details>


<details> <summary>Phase 2 and 3 tables</summary>

## `profile_reminder`

| Column Name   | Data Type                | Constraints  |
| ------------- | ------------------------ | ------------ |
| reminderID    | uuid                     | PK, not null | 
| userID        | uuid                     | not null     |
| dateLastRemind| timestamp with time zone | not null     |


CREATE TABLE whatsappThreads (
  id                 uuid        PRIMARY KEY DEFAULT uuid_generate_v4(),
  external_thread_id text        NOT NULL,                     -- WhatsApp’s thread or business ID
  name               text,                               -- optional for group chats
  is_group           boolean     DEFAULT false,               -- single user vs. group
  created_by         uuid        REFERENCES auth.users(id) ON DELETE SET NULL,
  created_at         timestamp   DEFAULT now(),
  updated_at         timestamp   DEFAULT now(),
  last_message_at    timestamp,                            -- for quick sorting
  last_message_body  text                                  -- snippet preview
);

CREATE TABLE whatsappThreadMembers (
  id             uuid      PRIMARY KEY DEFAULT uuid_generate_v4(),
  thread_id      uuid      REFERENCES whatsappThreads(id) ON DELETE CASCADE,
  user_id        uuid      REFERENCES auth.users(id)     ON DELETE CASCADE,
  phone_number   text      NOT NULL,                       -- user’s WhatsApp number
  joined_at      timestamp DEFAULT now()
);

CREATE TABLE whatsappMessages (
  id             uuid        PRIMARY KEY DEFAULT uuid_generate_v4(),
  thread_id      uuid        REFERENCES whatsappThreads(id) ON DELETE CASCADE,
  message_id     text        NOT NULL,                   -- WhatsApp’s message ID
  from_number    text        NOT NULL,
  to_number      text        NOT NULL,
  direction      text        NOT NULL,                   -- 'inbound' or 'outbound'
  body           text,                                 -- text content
  media_url      text,                                 -- if message includes image/audio/etc.
  timestamp      timestamp   NOT NULL,                  -- when user sent it
  status         text        DEFAULT 'received',        -- e.g. 'sent', 'delivered', 'read'
  created_at     timestamp   DEFAULT now()
);


## `communications`

| Column Name     | Data Type                | Constraints  |show in UI & example                             |
| --------------- | ------------------------ | ------------ |-------------------------------------------------|
| commsID         | uuid                     | PK, not null | No
| commsChannel    | text                     | nullable     | eg Whatsapp, Email
| commsChannelID  | text                     | nullable     | eg WhatsappIdentifier, email address
| commsContent    | jsonb                    | nullable     | content of the comms msg
| commsDate       | date                     | nullable     |
| commsFromEntity | text                     | nullable     | Agency A
| commsFromID     | uuid                     | nullable     | uuid of Agency A
| commsFromParty  | text                     | nullable     | Jason Tan
| commsFromPerson | text                     | nullable     | uuid of Jason Tan
| commsToEntity   | text                     | nullable     |
| commsToID       | uuid                     | nullable     |
| commsToParty    | text                     | nullable     |
| commsToPerson   | text                     | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| tenant          | text                     | not null     | No
| secClass        | ARRAY                    | nullable     | No
| blacklist       | ARRAY,UUID               | nullable     | No
| updatedAt       | timestamp with time zone | not null     | No
| updatedBy       | uuid                     | nullable     | No

</details>


<details> <summary>Deleted tables ----------------------------------------------</summary>

## `agency_staffs`

| Column Name   | Data Type                | Constraints  |
| ------------- | ------------------------ | ------------ |
| agencyStaffID | uuid                     | PK, not null |
| agencyID      | uuid                     | nullable     |
| userID        | uuid                     | nullable     |
| staffName     | text                     | nullable     |
| staffEmail    | text                     | nullable     |
| staffMobile   | numeric                  | nullable     |
| staffRole     | ARRAY                    | nullable     |
| personality   | ARRAY                    | nullable     |
| profilePicUrl | text                     | nullable     |
| multimedia    | ARRAY,UUID               | nullable     |
| tenant        | text                     | nullable     |
| secClass      | ARRAY                    | nullable     |
| blacklist     | ARRAY,UUID               | nullable     |
| updatedAt     | timestamp with time zone | nullable     |
| updatedBy     | uuid                     | nullable     |

## `case_actions`

| Column Name   | Data Type                | Constraints  |
| ------------- | ------------------------ | ------------ |
| caseActionsID | uuid                     | PK, not null |
| caseID        | uuid                     | nullable     |
| activity      | text                     | nullable     |
| actionUser    | ARRAY,UUID               | nullable     |
| actionAgency  | ARRAY,UUID               | nullable     |
| actionOthers  | ARRAY                    | nullable     |
| multimedia    | ARRAY,UUID               | nullable     |
| tenant        | text                     | nullable     |
| secClass      | ARRAY                    | nullable     |
| blacklist     | ARRAY,UUID               | nullable     |
| updatedAt     | timestamp with time zone | nullable     |
| updatedBy     | uuid                     | nullable     |

## `task_actions`

| Column Name   | Data Type                | Constraints  |show in UI & example                             |
| ------------- | ------------------------ | ------------ |-------------------------------------------------|
| taskActionsID | uuid                     | PK, not null | No
| taskID        | uuid                     | not null     | No
| activity      | text                     | nullable     |
| actionUsers   | ARRAY,UUID               | nullable     |
| actionAgency  | ARRAY,UUID               | nullable     |
| actionOthers  | ARRAY                    | nullable     |
| multimedia    | ARRAY,UUID               | nullable     |
| tenant        | text                     | nullable     | No
| secClass      | ARRAY                    | nullable     | No
| blacklist     | ARRAY                    | nullable     | No
| updatedAt     | timestamp with time zone | nullable     | No
| updatedBy     | uuid                     | nullable     | No


</details>