# LLM-post-call
It shows how to manage post call analysis.

## Transcribe의 Post-call Analytics를 이용한 변환

API Request는 아래와 같습니다. 

```java
{
    "CallAnalyticsJobName": "myPostCallTest",
    "Media": {
        "MediaFileUri": "s3://filesharing-ksdyb/post-call/sample-call-1.wav"
    },
    "Settings": {
        "LanguageOptions": [
            "en-US"
        ]
    },
    "ChannelDefinitions": [
        {
            "ChannelId": 1,
            "ParticipantRole": "AGENT"
        },
        {
            "ChannelId": 0,
            "ParticipantRole": "CUSTOMER"
        }
    ],
    "DataAccessRoleArn": "arn:aws:iam::677146750822:role/service-role/AmazonTranscribeServiceRoleFullAccess-TrascribeRoleForPostCall"
}
```

이때의 응답의 형태는 아래와 같습니다. response['Transcript'][0] 아래에 Content로 대화의 내용을 ParticipantRole로 대화의 상대를 확인할 수 있습니다.

![image](https://github.com/kyopark2014/LLM-post-call/assets/52392004/5cf05d92-ccfc-4fec-99c0-febd1b9a5e85)


## Reference
[boto3 - start_transcription_job](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/transcribe/client/start_transcription_job.html#)

[boto3 - start_job](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/amplify/client/start_job.html#)

[boto3 - start_call_analytics_job](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/transcribe/client/start_call_analytics_job.html)
