# Red Orchestra CloudFormation templates

## Linux Notes

- This fully starts, however steam auth doesn't work. I believe this is something to do with the app and SteamCMD. Many others have complained on forums of similar issues. If anyone has a solution, let me know.

## Windows Notes

- Currently this works correctly, but there are manual steps that haven't been scripted yet.
- I never scripted an auto-start, or service method for the game as I ran out of time, and didn't script the steam login either.

1. Install full steam client (downloaded automatically to c:\games)
2. Login to full steam client and leave running
3. Run game by running c:\games\start-ro.bat.

## Running the server

- You will need an SSH key created on AWS that you have access to.
- Change parameters as needed.
- t2.small, t3.small instances seem to be enough for 20-30 players. 50-64 player servers needed a powerful server back in the day, consider a c5 instance for these sorts of player counts.

```bash
aws cloudformation create-stack --template-body file://RO-EC2Instance-linux.yml --stack-name ro1-server-test-stack-al-1 --parameters ParameterKey=KeyName,ParameterValue=ro1-server-key ParameterKey=InstanceType,ParameterValue=t2.small ParameterKey=SteamUsername,ParameterValue=YOURSTEAMNAME ParameterKey=SteamPassword,ParameterValue=YOURSTEAMPASSWORD ParameterKey=ServerName,ParameterValue=YOURSERVERNAME ParameterKey=AdminPassword,ParameterValue=YOURADMINPASSWORD ParameterKey=MaxPlayers,ParameterValue=20
```

Delete Server:

```bash
aws cloudformation delete-stack --stack-name ro1-server-test-stack-al-1
```