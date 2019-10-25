# AWS token controller

## Why get-aws-session-token?

Yeah, I know that `aws sts get-session-token` exists.  My issue with it is that it dumps the output in JSON, which, is basically useless for me on the command line.

```
{
    "Credentials": {
        "SecretAccessKey": "XXXXXXXXXXXXXXXXXXXXXXXXXXXX",
        "SessionToken": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
        "Expiration": "2019-01-06T04:58:13Z",
        "AccessKeyId": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
    }
}
``` 


## Installation

No frills here, copy the get-aws-session-token file to your /usr/local/bin/ directory.  

## Command

I've got an alias in my `.zshrc` that is:
`alias -g getaws="get-aws-session-token export --serial-number arn:aws:iam::<IAM>:mfa/uid0 --token-code "` so that if I want a token, I can simply:
`getaws XXXXXX` and boom.  I've got a token.  

There's an OSX binary for now.  I'll probably build a Linux one over the weekend just to make my life easier.  Bonus points if you have your MFA token in a place where you can do this automatically in your login/initalization cycle, but, doing so is left up  to the exercise of the reader.  

## Output

`get-aws-session-token export --serial-number arn:aws:iam::<IAM>:mfa/uid0 --token-code XXXXXX` yields the following:

```
export AWS_SESSION_TOKEN=XXXXXXXXXXXXXXXXXXXXXXXXXXXX
export AWS_SECRET_ACCESS_KEY=XXXXXXXXXXXXXXXXXXXX
export AWS_ACCESS_KEY_ID=XXXXXXXXXXXXXXXXXXXX
```

Don't worry, if you screw it up, it'll tell you the right way to do it.

## Version

### version 0.1
Initialize `aws-session-token` command.
