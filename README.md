Resources:
  MyBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-bucket-name
  MyBucketPolicy:
    Type: AWS::S3::BucketPolicy
    Properties:
      Bucket: !Ref MyBucket
      PolicyDocument:
        Version: 2012-10-17
        Statement:
          - Sid: DenyPublicAccess
            Effect: Deny
            Principal: '*'
            Action: s3:GetObject
            Resource: !Sub arn:aws:s3:::${MyBucket}/*
            Condition:
              StringNotEquals:
                aws:PrincipalOrgID: "YOUR_ORGANIZATION_ID"
