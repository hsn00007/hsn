## `agency`

| Column Name     | Data Type                | Constraints  |
| --------------- | ------------------------ | ------------ |
| agency_id       | uuid                     | PK, not null |
| agencyName      | text                     | nullable     |
| address         | text                     | nullable     |
| agencyEmail     | text                     | nullable     |
| servicesOffered | ARRAY                    | nullable     |
| hotline         | numeric                  | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| div             | text                     | nullable     |
| secClass        | ARRAY                    | nullable     |
| blacklist       | ARRAY,UUID               | nullable     |
| updatedAt       | timestamp with time zone | nullable     |
| updatedBy       | uuid                     | nullable     |

## `agency_engagements`

| Column Name         | Data Type                | Constraints  |
| ------------------- | ------------------------ | ------------ |
| agencyEngagementsID | uuid                     | PK, not null |
| agencyID            | uuid                     | nullable     |
| engagementType      | ARRAY                    | nullable     |
| agencyStaffID       | uuid                     | nullable     |
| caseOfficer         | text                     | nullable     |
| caseOfficerMobile   | numeric                  | nullable     |
| engagementDetails   | text                     | nullable     |
| householdID         | ARRAY                    | nullable     |
| residentID          | ARRAY                    | nullable     |
| multimedia          | ARRAY,UUID               | nullable     |
| div                 | text                     | nullable     |
| secClass            | ARRAY                    | nullable     |
| blacklist           | ARRAY,UUID               | nullable     |
| updatedAt           | timestamp with time zone | nullable     |
| updatedBy           | uuid                     | nullable     |

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
| div           | text                     | nullable     |
| secClass      | ARRAY                    | nullable     |
| blacklist     | ARRAY,UUID               | nullable     |
| updatedAt     | timestamp with time zone | nullable     |
| updatedBy     | uuid                     | nullable     |

## `case`

| Column Name   | Data Type                | Constraints  |
| ------------- | ------------------------ | ------------ |
| caseID        | uuid                     | PK, not null |
| caseTitle     | text                     | nullable     |
| caseSummary   | text                     | nullable     |
| caseDetails   | text                     | nullable     |
| staffInCharge | uuid                     | nullable     |
| multimedia    | ARRAY,UUID               | nullable     |
| div           | text                     | nullable     |
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
| div           | text                     | nullable     |
| secClass      | ARRAY                    | nullable     |
| blacklist     | ARRAY,UUID               | nullable     |
| updatedAt     | timestamp with time zone | nullable     |
| updatedBy     | uuid                     | nullable     |

## `case_involvements`

| Column Name        | Data Type                | Constraints  |
| ------------------ | ------------------------ | ------------ |
| caseInvolvementsID | uuid                     | PK, not null |
| caseID             | uuid                     | nullable     |
| entityType         | text                     | nullable     |
| entityID           | uuid                     | nullable     |
| caseRole           | ARRAY                    | nullable     |
| description        | text                     | nullable     |
| multimedia         | ARRAY,UUID               | nullable     |
| div                | text                     | nullable     |
| secClass           | ARRAY                    | nullable     |
| blacklist          | ARRAY,UUID               | nullable     |
| updatedAt          | timestamp with time zone | nullable     |
| updatedBy          | uuid                     | nullable     |

## `case_statuses`

| Column Name    | Data Type                | Constraints  |
| -------------- | ------------------------ | ------------ |
| caseStatusesID | uuid                     | PK, not null |
| caseID         | uuid                     | nullable     |
| caseStatus     | text                     | nullable     |
| reasonStatus   | text                     | nullable     |
| statusDate     | date                     | nullable     |
| multimedia     | ARRAY,UUID               | nullable     |
| div            | text                     | nullable     |
| secClass       | ARRAY                    | nullable     |
| blacklist      | ARRAY,UUID               | nullable     |
| updatedAt      | timestamp with time zone | nullable     |
| updatedBy      | uuid                     | nullable     |

## `communications`

| Column Name     | Data Type                | Constraints  |
| --------------- | ------------------------ | ------------ |
| commsID         | uuid                     | PK, not null |
| commsChannel    | text                     | nullable     |
| commsChannelID  | text                     | nullable     |
| commsContent    | jsonb                    | nullable     |
| commsDate       | date                     | nullable     |
| commsFromEntity | text                     | nullable     |
| commsFromID     | uuid                     | nullable     |
| commsFromParty  | text                     | nullable     |
| commsFromPerson | text                     | nullable     |
| commsToEntity   | text                     | nullable     |
| commsToID       | uuid                     | nullable     |
| commsToParty    | text                     | nullable     |
| commsToPerson   | text                     | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| div             | text                     | not null     |
| secClass        | ARRAY                    | nullable     |
| blacklist       | ARRAY,UUID               | nullable     |
| updatedAt       | timestamp with time zone | not null     |
| updatedBy       | uuid                     | nullable     |

## `event`

| Column Name      | Data Type                | Constraints  |
| ---------------- | ------------------------ | ------------ |
| eventID          | uuid                     | PK, not null |
| eventTitle       | text                     | nullable     |
| eventDescription | text                     | nullable     |
| startDate        | date                     | nullable     |
| startTime        | time without time zone   | nullable     |
| endDate          | date                     | nullable     |
| endTime          | time without time zone   | nullable     |
| eventLocation    | text                     | nullable     |
| eventGeopoint    | text                     | nullable     |
| eventPosterUrl   | text                     | nullable     |
| multimedia       | ARRAY,UUID               | nullable     |
| div              | text                     | not null     |
| secClass         | ARRAY                    | nullable     |
| blacklist        | ARRAY,UUID               | nullable     |
| updatedAt        | timestamp with time zone | not null     |
| updatedBy        | uuid                     | nullable     |

## `event_activities`

| Column Name         | Data Type                | Constraints  |
| ------------------- | ------------------------ | ------------ |
| eventActivitiesID   | uuid                     | PK, not null |
| eventID             | uuid                     | nullable     |
| activityType        | ARRAY                    | nullable     |
| activityDescription | text                     | nullable     |
| entityType          | text                     | nullable     |
| entityID            | uuid                     | nullable     |
| userInvolved        | ARRAY,UUID               | nullable     |
| agencyInvolved      | ARRAY,UUID               | nullable     |
| multimedia          | ARRAY,UUID               | nullable     |
| div                 | text                     | nullable     |
| secClass            | ARRAY                    | nullable     |
| blacklist           | ARRAY,UUID               | nullable     |
| updatedAt           | timestamp with time zone | nullable     |
| updatedBy           | uuid                     | nullable     |

## `event_requirements`

| Column Name         | Data Type                | Constraints  |
| ------------------- | ------------------------ | ------------ |
| eventRequirementsID | uuid                     | PK, not null |
| eventID             | uuid                     | not null     |
| eventRequirement    | text                     | nullable     |
| startDate           | date                     | nullable     |
| startTime           | time with time zone      | nullable     |
| endDate             | date                     | nullable     |
| endTime             | time with time zone      | nullable     |
| requirementLocation | text                     | nullable     |
| meetingLocation     | text                     | nullable     |
| meetingDatetime     | timestamp with time zone | nullable     |
| userInvolved        | ARRAY,UUID               | nullable     |
| agencyInvolved      | ARRAY,UUID               | nullable     |
| externalVolunteers  | ARRAY                    | nullable     |
| multimedia          | ARRAY,UUID               | nullable     |
| div                 | text                     | nullable     |
| secClass            | ARRAY                    | nullable     |
| blacklist           | ARRAY,UUID               | nullable     |
| updatedAt           | timestamp with time zone | not null     |
| updatedBy           | uuid                     | nullable     |

## `household`

| Column Name    | Data Type                | Constraints  |
| -------------- | ------------------------ | ------------ |
| householdID    | uuid                     | PK, not null |
| block          | text                     | nullable     |
| floor          | text                     | nullable     |
| unit           | text                     | nullable     |
| street         | text                     | nullable     |
| postalcode     | character varying        | nullable     |
| unitName       | text                     | nullable     |
| buildingName   | text                     | nullable     |
| estateName     | text                     | nullable     |
| houseType      | text                     | nullable     |
| rn             | text                     | nullable     |
| race           | text                     | nullable     |
| religion       | text                     | nullable     |
| houseOwnership | text                     | nullable     |
| spokenLanguage | ARRAY                    | nullable     |
| incomeLevel    | text                     | nullable     |
| email          | text                     | nullable     |
| mobile         | numeric                  | nullable     |
| homePhone      | numeric                  | nullable     |
| personality    | ARRAY                    | nullable     |
| supportParty   | boolean                  | nullable     |
| supportAdvisor | boolean                  | nullable     |
| advisor        | text                     | nullable     |
| AdditionalInfo | text                     | nullable     |
| remarks        | text                     | nullable     |
| multimedia     | ARRAY,UUID               | nullable     |
| div            | text                     | nullable     |
| secClass       | ARRAY                    | nullable     |
| blacklist      | ARRAY,UUID               | nullable     |
| updatedAt      | timestamp with time zone | nullable     |
| updatedBy      | uuid                     | nullable     |

## `household_occupants`

| Column Name  | Data Type                | Constraints  |
| ------------ | ------------------------ | ------------ |
| occupantID   | uuid                     | PK, not null |
| householdID  | uuid                     | not null     |
| residentID   | uuid                     | not null     |
| familyRole   | text                     | nullable     |
| stillStaying | boolean                  | nullable     |
| multimedia   | ARRAY,,UUID              | nullable     |
| div          | text                     | nullable     |
| secClass     | ARRAY                    | nullable     |
| blacklist    | ARRAY,UUID               | nullable     |
| updatedAt    | timestamp with time zone | nullable     |
| updatedBy    | uuid                     | nullable     |

## `logs`

| Column Name  | Data Type                | Constraints  |
| ------------ | ------------------------ | ------------ |
| logsID       | uuid                     | PK, not null |
| action       | text                     | nullable     |
| tableUpdated | text                     | nullable     |
| fieldUpdated | text                     | nullable     |
| oldValue     | text                     | nullable     |
| newValue     | text                     | nullable     |
| div          | text                     | nullable     |
| secClass     | ARRAY                    | nullable     |
| blacklist    | ARRAY,UUID               | nullable     |
| updatedAt    | timestamp with time zone | nullable     |
| updatedBy    | uuid                     | nullable     |

## `multimedia`

| Column Name      | Data Type                | Constraints  |
| ---------------- | ------------------------ | ------------ |
| multimediaID     | uuid                     | PK, not null |
| mediaUrl         | text                     | nullable     |
| mediaType        | text                     | nullable     |
| mediaTitle       | text                     | nullable     |
| mediaDescription | text                     | nullable     |
| div              | text                     | nullable     |
| secClass         | ARRAY                    | nullable     |
| blacklist        | ARRAY,UUID               | nullable     |
| updatedAt        | timestamp with time zone | nullable     |
| updatedBy        | uuid                     | nullable     |

## `resident`

| Column Name     | Data Type                | Constraints  |
| --------------- | ------------------------ | ------------ |
| residentID      | uuid                     | PK, not null |
| residentID      | uuid                     | PK, not null |
| verbalName      | text                     | nullable     |
| officialName    | text                     | nullable     |
| officialID      | text                     | nullable     |
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
| supportParty    | boolean                  | nullable     |
| supportAdvisor  | boolean                  | nullable     |
| advisor         | text                     | nullable     |
| AdditionalInfo  | text                     | nullable     |
| remarks         | text                     | nullable     |
| multimedia      | ARRAY,UUID               | nullable     |
| div             | text                     | nullable     |
| secClass        | ARRAY                    | nullable     |
| blacklist       | ARRAY,UUID               | nullable     |
| updatedAt       | timestamp with time zone | nullable     |
| updatedBy       | uuid                     | nullable     |

## `task`

| Column Name   | Data Type                | Constraints  |
| ------------- | ------------------------ | ------------ |
| taskID        | uuid                     | PK, not null |
| caseID        | uuid                     | nullable     |
| task          | text                     | nullable     |
| agencyID      | uuid                     | nullable     |
| taskOfficer   | text                     | nullable     |
| officerMobile | numeric                  | nullable     |
| multimedia    | ARRAY,UUID               | nullable     |
| div           | text                     | nullable     |
| secClass      | ARRAY                    | nullable     |
| blacklist     | ARRAY,UUID               | nullable     |
| updatedAt     | timestamp with time zone | not null     |
| updatedBy     | uuid                     | nullable     |

## `task_actions`

| Column Name   | Data Type                | Constraints  |
| ------------- | ------------------------ | ------------ |
| taskActionsID | uuid                     | PK, not null |
| taskID        | uuid                     | not null     |
| activity      | text                     | nullable     |
| actionUsers   | ARRAY,UUID               | nullable     |
| actionAgency  | ARRAY,UUID               | nullable     |
| actionOthers  | ARRAY                    | nullable     |
| multimedia    | ARRAY,UUID               | nullable     |
| div           | text                     | nullable     |
| secClass      | ARRAY                    | nullable     |
| blacklist     | ARRAY                    | nullable     |
| updatedAt     | timestamp with time zone | nullable     |
| updatedBy     | uuid                     | nullable     |

## `task_statuses`

| Column Name    | Data Type                | Constraints  |
| -------------- | ------------------------ | ------------ |
| taskStatusesID | uuid                     | PK, not null |
| taskID         | uuid                     | not null     |
| taskStatus     | text                     | nullable     |
| statusReason   | text                     | nullable     |
| statusDate     | date                     | nullable     |
| multimedia     | ARRAY,UUID               | nullable     |
| div            | text                     | nullable     |
| secClass       | ARRAY                    | nullable     |
| blacklist      | ARRAY,UUID               | nullable     |
| updatedAt      | timestamp with time zone | nullable     |
| updatedBy      | uuid                     | nullable     |

## `user`

| Column Name    | Data Type                | Constraints  |
| -------------- | ------------------------ | ------------ |
| userID         | uuid                     | PK, not null |
| verbalName     | text                     | nullable     |
| officialName   | text                     | nullable     |
| officialID     | text                     | nullable     |
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
| div            | text                     | nullable     |
| secClass       | ARRAY                    | nullable     |
| blacklist      | ARRAY,UUID               | nullable     |
| updatedAt      | timestamp with time zone | nullable     |
| updatedBy      | uuid                     | nullable     |

## `staff_contributions`

| Column Name        | Data Type                | Constraints  |
| ------------------ | ------------------------ | ------------ |
| userID             | uuid                     | PK not null  |
| entityType         | text                     | nullable     |
| entityID           | uuid                     | nullable     |
| role               | ARRAY                    | nullable     |
| description        | text                     | nullable     |
| multimedia         | ARRAY,UUID               | nullable     |
| div                | text                     | nullable     |
| secClass           | ARRAY                    | nullable     |
| blacklist          | ARRAY,UUID               | nullable     |
| updatedAt          | timestamp with time zone | nullable     |
| updatedBy          | uuid                     | nullable     |


## `error`

| Column Name   | Data Type                | Constraints  |
| ------------- | ------------------------ | ------------ |
| errorID       | uuid                     | PK, not null |
| module        | text                     | nullable     |
| field         | text                     | nullable     |
| situation     | text                     | nullable     |
| errorMessage  | text                     | nullable     |
| userInvolved  | uuid                     | nullable     |
| datetimeError | timestamp with time zone | nullable     |
