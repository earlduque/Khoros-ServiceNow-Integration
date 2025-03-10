# Khoros-ServiceNow-Integration

## Public API Functions

### getMessageInfo
```typescript
getMessageInfo(messageId: string | string[]): Object | Object[]
```
Retrieves detailed message information from the Khoros API for one or more message IDs.

**Parameters:**
- `messageId`: A single message ID string or an array of message ID strings

**Returns:**
- Single message object or array of message objects containing the message details from Khoros

**Example Usage:**
```javascript
const khoros = new x_1468549_khoros_s.Khoros();

// Single message lookup
const singleMessage = khoros.getMessageInfo('12345');

// Multiple message lookup
const multipleMessages = khoros.getMessageInfo(['12345', '12345']);
```

---

### getKudos
```typescript
getKudos(messageId: string | string[]): Object | Object[]
```

Retrieves kudos information from the Khoros API for one or more message IDs.

**Parameters:**
- `messageId`: A single message ID string or an array of message IDs

**Returns:**
- Single kudos object or array of kudos objects containing the kudos details for the specified message(s)

**Example Usage:**
```javascript
const khoros = new x_1468549_khoros_s.Khoros();

// Single message kudos lookup
const singleMessageKudos = khoros.getKudos('1234567');

// Multiple message kudos lookup
const multipleMessageKudos = khoros.getKudos(['1234567', '1234567']);
```

---

### getReplies
```typescript
getReplies(messageId: string | string[]): Object | Object[]
```

Retrieves reply messages from the Khoros API for one or more message IDs.

**Parameters:**
- `messageId`: A single message ID string or an array of message IDs

**Returns:**
- Single object or array of objects containing the reply messages for the specified message(s)

**Example Usage:**
```javascript
const khoros = new x_1468549_khoros_s.Khoros();

// Single message replies lookup
const singleMessageReplies = khoros.getReplies('1234567');

// Multiple message replies lookup
const multipleMessageReplies = khoros.getReplies(['1234567', '1234567']);
```

---

### getUserInfoByEmail
```typescript
getUserInfoByEmail(email: string | string[]): Object | Object[]
```
Searches for user information in Khoros using email address(es).

**Parameters:**
- `email`: A single email address string or an array of email addresses

**Returns:**
- Single user object or array of user objects matching the email address(es)

**Example Usage:**
```javascript
const khoros = new x_1468549_khoros_s.Khoros();

// Single email lookup
const singleUser = khoros.getUserInfoByEmail('user@example.com');

// Multiple email lookup
const multipleUsers = khoros.getUserInfoByEmail(['user1@example.com', 'user2@example.com']);
```

---

### getUserInfoBySSOId
```typescript
getUserInfoBySSOId(SSOid: string | string[]): Object | Object[]
```
Retrieves user information from Khoros using SSO ID(s).

**Parameters:**
- `SSOid`: A single SSO ID string or an array of SSO IDs

**Returns:**
- Single user object or array of user objects matching the SSO ID(s)

**Example Usage:**
```javascript
const khoros = new x_1468549_khoros_s.Khoros();

// Single SSO ID lookup
const singleUser = khoros.getUserInfoBySSOId('(redacted)');

// Multiple SSO ID lookup
const multipleUsers = khoros.getUserInfoBySSOId(['(redacted)', '(redacted)']);
```

---

### getUserInfoByUserId
```typescript
getUserInfoByUserId(userId: string | string[]): Object | Object[]
```
Retrieves user information from Khoros using user ID(s).

**Parameters:**
- `userId`: A single user ID string or an array of user IDs

**Returns:**
- Single user object or array of user objects matching the user ID(s)

**Example Usage:**
```javascript
const khoros = new x_1468549_khoros_s.Khoros();

// Single user ID lookup
const singleUser = khoros.getUserInfoByUserId('12345');

// Multiple user ID lookup
const multipleUsers = khoros.getUserInfoByUserId(['12345', '12345']);
```

---

## Internal Helper Functions

### initialize
Internal initialization function that sets up the Khoros instance and retrieves the initial session token.

### handleArrayRequests
Internal utility function that handles processing of both single values and arrays for user information requests.

### getUserInfo
Internal function that makes the actual API request to search for user information based on a query string.

### getSessionToken
Internal authentication function that retrieves and sets up the session token required for API requests.

---

### Example user data we have access to

| Field Name             | Value                                                                                                                                                                                                                                          | JSON Path                                | Description / Notes                                               |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------- | ----------------------------------------------------------------- |
| User ID                | 12345                                                                                                                                                                                                                                          | data.id                                  | Internal user identifier.                                         |
| SSO ID                 | (redacted)                                                                                                                                                                                                                           | data.sso_id                              | ID from single sign-on provider.                                  |
| User Profile Link      | [https://www.servicenow.com/community/user/...](https://www.servicenow.com/community/user/... "https://www.servicenow.com/community/user/...")                                                                                                 | data.view_href                           | Direct link to the user’s profile page.                           |
| Login (Username)       | Earl Duque                                                                                                                                                                                                                                     | data.login                               | Display name / username.                                          |
| Email                  | (redacted)                                                                                                                                                                                                                      | data.email                               | User’s email address.                                             |
| First Name             | Earl                                                                                                                                                                                                                                           | data.first_name                          |
| Last Name              | Duque                                                                                                                                                                                                                                          | data.last_name                           |
| Biography              | Formerly ...                                                                                                                                                                                                                               | data.biography                           | Short user bio.                                                   |
| Online Status          | online                                                                                                                                                                                                                                         | data.online_status                       | Indicates if user is currently online, offline, or invisible.     |
| Banned                 | FALSE                                                                                                                                                                                                                                          | data.banned                              | Whether the user is banned from the community.                    |
| Deleted                | FALSE                                                                                                                                                                                                                                          | data.deleted                             | Whether the user’s account is fully removed.                      |
| Personal Info Privacy  | none                                                                                                                                                                                                                                           | data.personal_info_privacy               | Privacy setting for personal info (e.g., none, contacts, all).    |
| Email Address Privacy  | none                                                                                                                                                                                                                                           | data.email_address_privacy               | Privacy setting for email visibility.                             |
| Registration Time      | 2021-08-10T12:00:00.000-07:00                                                                                                                                                                                                                  | data.registration_data.registration_time | Date/time user registered.                                        |
| Registration Status    | fully-registered                                                                                                                                                                                                                               | data.registration_data.status            | E.g., fully-registered, pending.                                  |
| Last Visit Time        | 2025-02-19T16:57:00.433-08:00                                                                                                                                                                                                                  | data.last_visit_time                     | Timestamp of user’s most recent visit.                            |
| Language               | en                                                                                                                                                                                                                                             | data.language                            | User’s chosen interface language.                                 |
| Avatar (Profile Image) | [https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/...](https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/... "https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/...") | data.avatar.profile                      | The main (largest) avatar URL.                                    |
| Rank (Name)            | Administrator                                                                                                                                                                                                                                  | data.rank.name                           | The user’s rank/title in the community.                           |
| Rank (Color)           | FCA822                                                                                                                                                                                                                                         | data.rank.color                          | Associated color code, possibly used for styling.                 |
| Rank (Status)          | active                                                                                                                                                                                                                                         | data.rank.rank_status                    | E.g., active, inactive.                                           |
| Minutes Online         | 31051                                                                                                                                                                                                                                          | data.metrics.minutes_online              | Total minutes user has spent logged in (“online”).                |
| Number of Logins       | 427                                                                                                                                                                                                                                            | data.metrics.logins                      | How many times the user has signed in.                            |
| Number of Posts        | 138                                                                                                                                                                                                                                            | data.metrics.posts                       | How many messages/posts this user has authored.                   |
| Page Views             | 5551                                                                                                                                                                                                                                           | data.metrics.page_views                  | How many pages (or threads) the user has viewed.                  |
| Messages Read          | 7504                                                                                                                                                                                                                                           | data.metrics.messages_read               | Number of individual messages the user has read.                  |
| Private Msgs Received  | 2                                                                                                                                                                                                                                              | data.metrics.private_messages_received   | Number of private/direct messages received.                       |
| Private Msgs Sent      | 0                                                                                                                                                                                                                                              | data.metrics.private_messages_sent       | Number of private/direct messages sent.                           |
| Show User Signatures   | TRUE                                                                                                                                                                                                                                           | data.show_user_signatures                | Whether user signatures are displayed when user posts.            |
| Online Status Privacy  | all                                                                                                                                                                                                                                            | data.online_status_privacy               | Who can see the user’s online status (e.g., all, none, contacts). |

---

| Badge # | Badge ID | Badge Title                    | Earned Date                   | Description                                                                         |
| ------- | -------- | ------------------------------ | ----------------------------- | ----------------------------------------------------------------------------------- |
| 1       | 44       | ServiceNow Employee            | 2022-10-01T08:04:35.708-07:00 | ServiceNow Employee                                                                 |
| 2       | 30       | Helpful Answers 300            | 2024-09-09T11:15:10.221-07:00 | Community members who have 300 answers marked Helpful                               |
| 3       | 29       | Helpful Answers 200            | 2024-03-22T10:26:35.069-07:00 | Community members who have 200 answers marked Helpful                               |
| 4       | 28       | Helpful Answers 150            | 2024-01-10T23:19:39.303-08:00 | Community members who have 150 answers marked Helpful                               |
| 5       | 27       | Helpful Answers 100            | 2023-11-05T01:22:54.370-07:00 | Community members who have 100 answers marked Helpful                               |
| 6       | 26       | Helpful Answers 75             | 2023-10-22T21:16:45.502-07:00 | Community members who have 75 answers marked Helpful                                |
| 7       | 25       | Helpful Answers 50             | 2023-10-04T00:20:51.664-07:00 | Community members who have 50 answers marked Helpful                                |
| 8       | 24       | Helpful Answers 25             | 2023-03-22T16:01:27.895-07:00 | Community members who have 25 answers marked Helpful                                |
| 9       | 23       | Helpful Answers 10             | 2022-09-30T08:46:08.779-07:00 | Community members who have 10 answers marked Helpful                                |
| 10      | 22       | Helpful Answers 5              | 2022-09-30T08:46:14.279-07:00 | Community members who have 5 answers marked Helpful                                 |
| 11      | 64       | Hacktoberfest 2024 Participant | 2024-11-25T14:48:45.828-08:00 | Awarded to participants that completed the ServiceNow Hacktoberfest 2024 Challenge. |

### User info response sample

```json
[
  {
    "status": "success",
    "message": "",
    "http_code": 200,
    "data": {
      "type": "users",
      "list_item_type": "user",
      "size": 1,
      "items": [
        {
          "type": "user",
          "id": "12345",
          "sso_id": "(redacted)",
          "href": "/users/12345",
          "view_href": "https://www.servicenow.com/community/user/viewprofilepage/user-id/12345",
          "login": "Earl Duque",
          "email": "(redacted)",
          "remember_password": true,
          "first_name": "Earl",
          "last_name": "Duque",
          "biography": "Formerly UCSD, UC Davis, KLOVE/Air1, and UCLA. Now a Developer Advocate for ServiceNow",
          "online_status": "offline",
          "personal_info_privacy": "none",
          "email_address_privacy": "none",
          "online_status_privacy": "all",
          "rank": {
            "type": "rank",
            "id": "1",
            "name": "Administrator",
            "position": 1,
            "bold": true,
            "color": "FCA822",
            "roles_granted": {
              "query": "SELECT * FROM roles WHERE ranks_granting.id = '1'"
            },
            "roles_removed": {
              "query": "SELECT * FROM roles WHERE ranks_removing.id = '1'"
            },
            "icon_left": "/i/rank_icons/admin.gif",
            "formula_enabled": false,
            "formula": "",
            "simple_criteria": {
              "type": "simple_rank_criteria",
              "role": {
                "type": "role",
                "id": "t:Administrator",
                "href": "/roles/t:Administrator"
              },
              "user": {},
              "number_of_posts": 0,
              "number_of_page_views": 0,
              "number_of_signins": 0,
              "minutes_online": 0,
              "minutes_since_registering": 0,
              "simple_formula": "hasRole(\"Administrator\")"
            },
            "rank_status": "active"
          },
          "avatar": {
            "type": "avatar",
            "profile": "https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/79a7e39d1b42fc981e579979b04bcb34.jpg",
            "message": "https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/79a7e39d1b42fc981e579979b04bcb34.jpg",
            "inline": "https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/79a7e39d1b42fc981e579979b04bcb34.jpg",
            "favicon": "https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/79a7e39d1b42fc981e579979b04bcb34.jpg",
            "print": "https://www.servicenow.com/community/s/legacyfs/online/avatars_servicenow/79a7e39d1b42fc981e579979b04bcb34.jpg"
          },
          "kudos_received": {
            "query": "SELECT * FROM kudos WHERE message.author.id = '12345'"
          },
          "kudos_given": {
            "query": "SELECT * FROM kudos WHERE user.id = '12345'"
          },
          "solutions_authored": {
            "query": "SELECT * FROM messages WHERE author.id = '12345' AND is_solution = true"
          },
          "topics": {
            "query": "SELECT * FROM messages WHERE author.id = '12345' AND depth = 0"
          },
          "threads_participated": {
            "query": "SELECT * FROM messages WHERE participants.id = '12345' AND depth = 0"
          },
          "images": {
            "query": "SELECT * FROM images WHERE owner.id = '12345'"
          },
          "public_images": {
            "query": "SELECT * FROM images WHERE owner.id = '12345' AND album.privacy_level = 'public' AND visibility = 'public'"
          },
          "albums": {
            "query": "SELECT * FROM albums WHERE owner.id = '12345'"
          },
          "videos": {
            "query": "SELECT * FROM videos WHERE owner.id = '12345'"
          },
          "user_badges": {
            "list_item_type": "user_badge",
            "size": 11,
            "items": [
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "44",
                  "description": "ServiceNow Employee",
                  "title": "ServiceNow Employee",
                  "icon_url": "https://www.servicenow.com/community/s/html/@7949A21E15D6FB4B0229C45DA89E4363/badge_icons/Community%20Badge%20-%20ServiceNow%20Employee.svg",
                  "awarded": 24359,
                  "activation_date": "2022-10-01T07:32:38.036-07:00"
                },
                "earned_date": "2022-10-01T08:04:35.708-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "30",
                  "description": "Community members who have 300 answers marked Helpful",
                  "title": "Helpful Answers 300",
                  "icon_url": "https://www.servicenow.com/community/s/html/@DDF9670EC9E7733C66D85972D17EDA03/badge_icons/Community%20Badge%20-%20Helpful%20Answers%20300.svg",
                  "awarded": 277,
                  "activation_date": "2022-09-30T08:45:21.583-07:00"
                },
                "earned_date": "2024-09-09T11:15:10.221-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "29",
                  "description": "Community members who have 200 answers marked Helpful",
                  "title": "Helpful Answers 200",
                  "icon_url": "https://www.servicenow.com/community/s/html/@EDA632A9687673677E94B437BC83D12E/badge_icons/Community%20Badge%20-%20Helpful%20Answers%20200.svg",
                  "awarded": 417,
                  "activation_date": "2022-09-30T08:45:30.547-07:00"
                },
                "earned_date": "2024-03-22T10:26:35.069-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "28",
                  "description": "Community members who have 150 answers marked Helpful",
                  "title": "Helpful Answers 150",
                  "icon_url": "https://www.servicenow.com/community/s/html/@C48EFA919D0B093AA5F46184953ADB41/badge_icons/Community%20Badge%20-%20Helpful%20Answers%20150.svg",
                  "awarded": 553,
                  "activation_date": "2022-09-30T08:45:36.095-07:00"
                },
                "earned_date": "2024-01-10T23:19:39.303-08:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "27",
                  "description": "Community members who have 100 answers marked Helpful",
                  "title": "Helpful Answers 100",
                  "icon_url": "https://www.servicenow.com/community/s/html/@5DE9B0FF5E328A244DAC8851FEB21188/badge_icons/Community%20Badge%20-%20Helpful%20Answers%20100.svg",
                  "awarded": 786,
                  "activation_date": "2022-09-30T08:45:41.022-07:00"
                },
                "earned_date": "2023-11-05T01:22:54.370-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "26",
                  "description": "Community members who have 75 answers marked Helpful",
                  "title": "Helpful Answers 75",
                  "icon_url": "https://www.servicenow.com/community/s/html/@263C563D88BFADF04C39545D3B043A0B/badge_icons/Community%20Badge%20-%20Helpful%20Answers%2075.svg",
                  "awarded": 1043,
                  "activation_date": "2022-09-30T08:45:48.167-07:00"
                },
                "earned_date": "2023-10-22T21:16:45.502-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "25",
                  "description": "Community members who have 50 answers marked Helpful",
                  "title": "Helpful Answers 50",
                  "icon_url": "https://www.servicenow.com/community/s/html/@493A36306B257F90651153FEE33CD9BF/badge_icons/Community%20Badge%20-%20Helpful%20Answers%2050.svg",
                  "awarded": 1499,
                  "activation_date": "2022-09-30T08:45:53.933-07:00"
                },
                "earned_date": "2023-10-04T00:20:51.664-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "24",
                  "description": "Community members who have 25 answers marked Helpful",
                  "title": "Helpful Answers 25",
                  "icon_url": "https://www.servicenow.com/community/s/html/@4F8B3D1A974BB550CB9407ADC74A198A/badge_icons/Community%20Badge%20-%20Helpful%20Answers%2025.svg",
                  "awarded": 2680,
                  "activation_date": "2022-09-30T08:45:59.538-07:00"
                },
                "earned_date": "2023-03-22T16:01:27.895-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "23",
                  "description": "Community members who have 10 answers marked Helpful",
                  "title": "Helpful Answers 10",
                  "icon_url": "https://www.servicenow.com/community/s/html/@E06E8758D5032A21D39B71425BE5D6AE/badge_icons/Community%20Badge%20-%20Helpful%20Answers%2010.svg",
                  "awarded": 5726,
                  "activation_date": "2022-09-30T08:46:05.877-07:00"
                },
                "earned_date": "2022-09-30T08:46:08.779-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "22",
                  "description": "Community members who have 5 answers marked Helpful",
                  "title": "Helpful Answers 5",
                  "icon_url": "https://www.servicenow.com/community/s/html/@E0E96579935625D9BB40175276799B62/badge_icons/Community%20Badge%20-%20Helpful%20Answers%205.svg",
                  "awarded": 9983,
                  "activation_date": "2022-09-30T08:46:10.872-07:00"
                },
                "earned_date": "2022-09-30T08:46:14.279-07:00"
              },
              {
                "type": "user_badge",
                "badge": {
                  "type": "badge",
                  "id": "64",
                  "description": "Awarded to participants that completed the ServiceNow Hacktoberfest 2024 Challenge.",
                  "title": "Hacktoberfest 2024 Participant",
                  "icon_url": "https://www.servicenow.com/community/s/html/@4D7354BBC6CD9ACFF56B2FE91FCBAE68/badge_icons/Community%20Badge%20-%20Event%20-%20Hacktoberfest%2024_300px-Recovered.png",
                  "awarded": 75,
                  "activation_date": "2024-11-25T14:47:25.232-08:00"
                },
                "earned_date": "2024-11-25T14:48:45.828-08:00"
              }
            ]
          },
          "following": {
            "query": "SELECT * FROM users WHERE followers.id = '12345'"
          },
          "followers": {
            "query": "SELECT * FROM users WHERE following.id = '12345'"
          },
          "language": "en",
          "show_user_signatures": "true",
          "metrics": {
            "type": "user_metrics",
            "logins": 434,
            "minutes_online": 31376,
            "posts": 138,
            "private_messages_received": 2,
            "private_messages_sent": 0,
            "page_views": 5591,
            "messages_read": 7639
          },
          "settings": {
            "query": "SELECT * FROM settings WHERE user.id = '12345'"
          },
          "registration_data": {
            "type": "registration_data",
            "registration_time": "2021-08-10T12:00:00.000-07:00",
            "status": "fully-registered",
            "registration_access_level": "all",
            "confirm_email_status": true,
            "sso_registration_fields": []
          },
          "mailbox": {
            "type": "mailbox"
          },
          "banned": false,
          "deleted": false,
          "roles": {
            "query": "SELECT * FROM roles WHERE users.id = '12345'"
          },
          "messages": {
            "query": "SELECT * FROM messages WHERE author.id = '12345'"
          },
          "reviews": {
            "query": "SELECT * FROM reviews WHERE author.id = '12345'"
          },
          "last_visit_time": "2025-03-01T09:22:00.925-08:00",
          "date_pattern": "MM-dd-yyyy",
          "friendly_date_enabled": true,
          "friendly_date_max_age": 31,
          "c_timezone": "US/Pacific",
          "c_uuid": "11ebfa07e9eb94d588540637b415ed111TWF"
        }
      ]
    },
    "metadata": {}
  }
]
```

### Message info response sample

```json
[
  {
    "status": "success",
    "message": "",
    "http_code": 200,
    "data": {
      "type": "message",
      "id": "1234567",
      "href": "/messages/1234567",
      "view_href": "https://www.servicenow.com/community/developer-advocate-blog/eample/ba-p/1234567",
      "author": {
        "type": "user",
        "id": "12345",
        "href": "/users/12345",
        "view_href": "https://www.servicenow.com/community/user/viewprofilepage/user-id/12345",
        "login": "Earl Duque"
      },
      "subject": "Now Assist for Code: Autocomplete, Code Explain & More!",
      "body": "<!--EXAMPLE. HTML BLOCK WOULD APPEAR HERE-->",
      "teaser": "",
      "board": {
        "type": "board",
        "id": "developer-advocate-blog",
        "href": "/boards/developer-advocate-blog",
        "view_href": "https://www.servicenow.com/community/developer-advocate-blog/bg-p/developer-advocate-blog"
      },
      "conversation": {
        "type": "conversation",
        "id": "1234567",
        "href": "/conversations/1234567",
        "view_href": "https://www.servicenow.com/community/developer-advocate-blog/example/ba-p/1234567",
        "style": "blog",
        "thread_style": "blog",
        "messages_count": 3,
        "solved": false,
        "last_post_time": "2025-02-27T07:08:02.754-08:00",
        "last_post_time_friendly": "Thursday"
      },
      "topic": {
        "type": "message",
        "id": "1234567",
        "href": "/messages/1234567",
        "view_href": "https://www.servicenow.com/community/developer-advocate-blog/example/ba-p/1234567"
      },
      "post_time": "2025-02-14T00:01:24.656-08:00",
      "post_time_friendly": "3 weeks ago",
      "depth": 0,
      "read_only": false,
      "edit_frozen": false,
      "language": "EN",
      "can_accept_solution": false,
      "placeholder": false,
      "is_solution": false,
      "solution_data": {},
      "metrics": {
        "type": "message_metrics",
        "views": 454
      },
      "current_revision": {
        "type": "revision",
        "id": "1234567_2",
        "last_edit_author": {
          "type": "user",
          "id": "12345",
          "href": "/users/12345",
          "view_href": "https://www.servicenow.com/community/user/viewprofilepage/user-id/12345",
          "login": "Earl Duque"
        },
        "last_edit_time": "2025-02-14T09:54:45.226-08:00"
      },
      "kudos": {
        "query": "SELECT * FROM kudos WHERE message.id = '1234567'"
      },
      "tags": {
        "query": "SELECT * FROM tags WHERE messages.id = '1234567'"
      },
      "labels": {
        "query": "SELECT * FROM labels WHERE messages.id = '1234567'"
      },
      "images": {
        "query": "SELECT * FROM images WHERE messages.id = '1234567'"
      },
      "videos": {
        "query": "SELECT * FROM videos WHERE messages.id = '1234567'"
      },
      "attachments": {
        "query": "SELECT * FROM attachments WHERE message.id = '1234567'"
      },
      "replies": {
        "query": "SELECT * FROM messages WHERE parent.id = '1234567'"
      },
      "ratings": {
        "query": "SELECT * FROM ratings WHERE message.id = '1234567'"
      },
      "custom_tags": {
        "query": "SELECT * FROM custom_tags WHERE messages.id = '1234567'"
      },
      "moderation_status": "approved",
      "visibility_scope": "public",
      "user_context": {
        "type": "user_context",
        "kudo": false,
        "read": false,
        "can_reply": true,
        "can_kudo": true,
        "can_delete": true
      },
      "device_id": "google_chrome_131",
      "popularity": 0.0005541208793294512,
      "excluded_from_kudos_leaderboards": false,
      "latest_version": {
        "type": "friendly_version",
        "major": "2",
        "minor": "0"
      },
      "include_hidden_messages": true,
      "content_workflow": {
        "type": "content_workflow",
        "state": "publish",
        "message_draft_history": {
          "query": "SELECT * FROM message_draft_history WHERE message.id = '1234567'"
        },
        "user_context": {
          "type": "message_workflow_context",
          "can_edit": true,
          "can_schedule": true
        },
        "view_href": "https://www.servicenow.com/community/blogs/blogworkflowpage/blog-id/developer-advocate-blog/article-id/1296"
      },
      "is_promoted": false
    },
    "metadata": {}
  }
]
```
