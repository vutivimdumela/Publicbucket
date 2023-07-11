Resources:
  NewKeyPair:
    Type: 'AWS::EC2::KeyPair'
    Properties:
      KeyName: MyKeyPair
  Ec2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: ami-02b92c281a4d3dc79
      KeyName: !Ref NewKeyPair
