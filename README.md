# Publicbucket
Resources:
  MyBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: Bucket-001
  MyBucketPolicy:
    Type: AWS::S3::BucketPolicy
    Properties:
      Bucket: !Ref MyBucket
      PolicyDocument:
        Version: 2012-10-17
        Statement:
          - Sid: PublicReadGetObject
            Effect: Allow
            Principal: '*'
            Action: s3:GetObject
            Resource: !Sub arn:aws:s3:::${MyBucket}/*
