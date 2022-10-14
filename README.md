# AssemblyAI CLI

![GitHub release (latest by date)](https://img.shields.io/github/v/release/assemblyai/assemblyai-cli) ![GitHub go.mod Go version](https://img.shields.io/github/go-mod/go-version/assemblyai/assemblyai-cli) ![GitHub](https://img.shields.io/github/license/assemblyai/assemblyai-cli)

A quick and easy way to test AssemblyAI's transcription features on your terminal

## Quickstart

1. Install the CLI with any of the methods described below
2. Add your token by executing `assemblyai config <YOUT-TOKEN>`
3. Get started transcribing any local, URL or YouTube audio or video by running

    ``` bash
    assemblyai transcribe https://youtu.be/BivrdU9xcIo --auto_chapters --auto_highlights --content_moderation --entity_detection --redact_pii --redact_pii_policies=drug,number_sequence,person_name --sentiment_analysis --topic_detection
    ```

## Installation

To install AssemblyAI CLI, use any of the following methods:

- ### Homebrew (macOS only)

  For macOS users, you can install via:

    ``` bash
    brew tap assemblyai/assemblyai
    brew install assemblyai
    ```

- ### Curl
  
  - Linux or macOS:
    Paste that in a Terminal or shell prompt.

      ``` bash
      /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/AssemblyAI/assemblyai-cli/main/install.sh)"
      ```

  - Windows Powershell:
    Paste that in a Terminal or shell prompt.

      ``` PowerShell
      Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Needed to run a remote script the first time
      iex "$(curl https://raw.githubusercontent.com/AssemblyAI/assemblyai-cli/main/install.ps1)"
      New-Alias -Name assemblyai -Value C:\\'./Program Files\'/AssemblyAI/assemblyai.exe # Needed to add the alias of the command, skip if already added
      ```

## Commands

- `config`: Use the config command to store your authentication token and automatically use it in any subsequent request.
Ex:

  ``` bash
  assemblyai config <token>
  ```

- `transcribe`: Runs the transcription of a local or URL file with all the features specified by the flags.
  Ex:

  ``` bash
  assemblyai transcribe <path | url | youtube url> [flags]
  ```

- `get`: Retrieves a previously transcribed file.
  Ex:

  ``` bash
  assemblyai get <transcription id> [flags]
  ```

## Flags

| Name | Abbreviation | Default | Description |
 |--|--|--|--|
|--json|-j|false|If true, the CLI will output the JSON. |
|--poll|-p|true|The CLI will poll the transcription every 3 seconds until it's complete.|
|--auto_chapters|-s|false|A "summary over time" for the audio file transcribed.|
|--auto_highlights|-a|false|Automatically detect important phrases and words in the text.|
|--content_moderation|-c|false|Detect if sensitive content is spoken in the file.|
|--dual_channel|-d|false|Enable dual channel|
|--entity_detection|-e|false|Identify a wide range of entities that are spoken in the audio file.|
|--format_text|-f|true|Enable text formatting|
|--punctuate|-u|true|Enable automatic punctuation|
|--redact_pii_policies|-i|drug,number_sequence,person_name|The list of PII policies to redact (source), comma-separated. Required if the redact_pii flag is true, with the default value including drugs, number sequences, and person names. |
|--redact_pii|-r|false|Remove personally identifiable information from the transcription.|
|--sentiment_analysis|-x|false|Detect the sentiment of each sentence of speech spoken in the file.|
|--speaker_labels|-l|true|Automatically detect the number of speakers in the file.|
|--topic_detection|-t|false|Label the topics that are spoken in the file.|
|--webhook_auth_header_name|-b|null|Containing the header's name which will be inserted into the webhook request|
|--webhook_auth_header_value|-o|null|The value of the header that will be inserted into the webhook request.|
|--webhook_url|-w|null|Receive a webhook once your transcript is complete.|
