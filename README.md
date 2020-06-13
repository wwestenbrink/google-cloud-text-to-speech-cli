# google-cloud-text-to-speech-cli

Command line interface for using the Google Cloud text-to-speech API to convert text into Linear PCM audio.

> Cloud Text-to-Speech Client Libraries  ｜  Cloud Text-to-Speech API  ｜  Google Cloud  
> https://cloud.google.com/text-to-speech/docs/

# How to use

## Export environment value

```
export GOOGLE_APPLICATION_CREDENTIALS=/path/to/credential.json
```

#### Google Service Account

Credential file of Google Service Account ( /path/to/credential.json ) is required.
If you don't have account, you need create it.


## Execute

Download latest application based on your platform.

> Releases · wwestenbrink/google-cloud-text-to-speech-cli  
> https://github.com/wwestenbrink/google-cloud-text-to-speech-cli/releases

```
// Show help
$ ./google-cloud-text-to-speech-cli --help
Usage:
  google-cloud-text-to-speech-cli [OPTIONS]

Application Options:
  -t, --text=          Text content.
  -f, --textFile=      Text file path.
  -l, --language=      LanguageCode. (default: en)
  -g, --gender=        SsmlGender. (default: FEMALE)
  -v, --voice=         Voice type. [ see --listvoicetype, --gender is ignored. ]
  -s, --rate=          SpeakingRate. [ 0.25 <= rate <= 4.0 ] (default: 1.0)
  -p, --pitch=         Pitch. [ -20.0 <= pitch <= 20.0 ]  (default: 0.0)
  -a, --audioProfile=  Audio effect profile to use (default: none)
  -o, --output=        Output file path. (default: out/output.mp3)
      --listvoicetype  Display voice types.
      --filterbylang   Filter voice types by language.

Help Options:
  -h, --help           Show this help message  



// Run
$ ./google-cloud-text-to-speech-cli --text="Thank you download my app. This is Command line interface for google-cloud-text-to-speech-api." --rate=1.5 --pitch=-5.0
language:  en
gender:  FEMALE
speakingRate:  1.5
pitch:  -5
output:  out/output.wav

Audio content written to file: out/output.wav
```

## Development

- go 1.13 ( or later )

> googleapis/google-cloud-go： Google Cloud Client Libraries for Go.  
> https://github.com/googleapis/google-cloud-go

#### Create `Service Account Key`

> Cloud Text-to-Speech Client Libraries  ｜  Cloud Text-to-Speech API  ｜  Google Cloud  
> https://cloud.google.com/text-to-speech/docs/reference/libraries#setting_up_authentication

Then, download credential json.

```
2019/09/23 20:00:08 rpc error: code = PermissionDenied desc = Cloud Text-to-Speech API has not been used in project xxxxxx before or it is disabled. 
Enable it by visiting https://console.cloud.google.com/apis/api/texttospeech.googleapis.com/overview?project=xxxxx then retry. 
If you enabled this API recently, wait a few minutes for the action to propagate to our systems and retry.
```

And enable API account ( register your credit card info ).

## Release

```
// release new version
git tag v0.0.3 && git push --tags && goreleaser --rm-dist
```

## References
> Basics 
> https://cloud.google.com/text-to-speech/docs/basics

> Supported voices and languages 
> https://cloud.google.com/text-to-speech/docs/voices

> Configure rate, pitch and audio profile
> https://cloud.google.com/text-to-speech/docs/reference/rest/v1/text/synthesize#audioconfig