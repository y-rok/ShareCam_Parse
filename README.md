# ShareCam_Parse

cloud code for parse


# API 

### Parse - API

| Name | Description| parameter |Error Code |
| ------------- | ----------- | ----------- |----------- |
| send message for verifying phone number | /sm_phone_verify| phone | 200 |
| confirm verification number for phone number and save userPhone |  /sm_phone_confirm| vNumber | 201,202 |
| complete sign up process | /sign_up_completed | | | 
| find phone number which hasn't been added to friend list yet and add it to friend list    | /sync_all_contact | | | 
| delete all of contacts createdby user | /delete_contact | | |
| 서버와 친구 목록 동기화 후 (추가, 수정, 삭제된 친구목록을 응답) | /sync_friend_list| | |

# ERROR CODE

|Code|Description| 
| ------------- | ----------- |
| 1 |  invalid parameter   |
| 200 | invalid phone number |
| 201 | verification number is not matched |
| 202 | phone number already exist |

# Class

## Field of Class [Local]

#### UploadingPicture

| field | description |
| ------------- | ----------- |
| pictureId | the object id of picture |
| state | the state of uploading a picture  [ -1 - uploading fail / 0 - standby uploading / 1 - uploading / 2 - uploading success  |
| percent | the percetage of uploading when the state is uploading |

## Field of Class [Remote]

#### Picture

- create
  - when you upload a picture, you should make object whose hasphoto field is "true" and photoSynched is "false".
  - And then you should try updating image field.
  - if you have done , you will have to change the field of photoSynched to "true" and thumnail image will be automatically generated

- expired (사진 저장 후 n일이 지난 경우)
  - hasPhoto = false / photoSynched = false


| field | description |
| ------------- | ----------- |
| createdBy |the user object id who create this picture|
| phoneList | the array of phone numbers which this picture should be shared with (해당 번호의 사용자가 가입 시 해당 phone number를 지우고 friendList의 friend objectId를 추가 한다)|
| groupList | the array of group objectId...| 
| friendList | the array of friend objectId | 
| image | file of a picture | 
| thumImage | thumnail  file (nX128px) |
| hasPhoto | true if this object should have a picture |
| photoSynched | true if image filed has a picture file |
| savedBy | the array of users who save the image |




## ACL of Class

#### _User
- create, get, find  - public access
- update , delete - only accessed by current user
- update , delete (with phone field) - only accessed by using master key 

#### Contact

#### Friend
- create, get, find, update, delete - only accessed by current user

##### Picture



  
