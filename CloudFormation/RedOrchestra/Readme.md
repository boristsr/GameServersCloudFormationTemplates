
Create Server:

```bash
aws cloudformation create-stack --template-body file://RO-EC2Instance-linux.yml --stack-name ro1-server-test-stack-al-1 --parameters ParameterKey=KeyName,ParameterValue=ro1-server-key ParameterKey=InstanceType,ParameterValue=t2.small ParameterKey=ImageResourceId,ParameterValue=ami-08fdde86b93accf1c ParameterKey=SteamUsername,ParameterValue=YOURSTEAMNAME ParameterKey=SteamPassword,ParameterValue=YOURSTEAMPASSWORD ParameterKey=ServerName,ParameterValue=RO-AusLockdownTest ParameterKey=AdminPassword,ParameterValue=YOURADMINPASSWORD ParameterKey=MaxPlayers,ParameterValue=20
```

Delete Server:

```bash
aws cloudformation delete-stack --stack-name ro1-server-test-stack-al-1
```