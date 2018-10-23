# Using Text\-to\-Speech with Amazon Connect<a name="text-to-speech"></a>

Amazon Connect supports text\-to\-speech, including SSML or plaintext with \(or without\) dynamic attributes\. You can enter text\-to\-speech prompts in any of the contact flow blocks that support prompt entry, such as **Play prompt** and **Get customer input**\. The text\-to\-speech voice is selected in the **Set voice** contact block\. You can also use SSML in Amazon Lex bots to modify the voice used by a chat bot when interacting with your customers\. For more information about using SSML in Amazon Lex bots, see [Managing Messages](https://docs.aws.amazon.com/lex/latest/dg//howitworks-manage-prompts.html#msg-prompts-response) and [Managing Conversation Context](https://docs.aws.amazon.com/lex/latest/dg//context-mgmt.html#special-response) in the Amazon Lex Developer Guide\.

Amazon Connect uses Amazon Polly, a service that converts text into lifelike speech using Speech Synthesis Markup Language \(SSML\)\. For more information, see [Using SSML](https://docs.aws.amazon.com/polly/latest/dg/ssml.html) in the Amazon Polly Developer Guide\.

SSML\-enhanced input text gives you more control over how Amazon Connect generates speech from the text you provide\. You can customize and control aspects of speech such as pronunciation, volume, and speed\. Amazon Polly provides this level of control using a subset of the SSML markup tags as defined by [Speech Synthesis Markup Language \(SSML\) Version 1\.1, W3C Recommendation](https://www.w3.org/TR/2010/REC-speech-synthesis11-20100907/)\.

## Modify a Prompt using SSML<a name="ssml-prompt"></a>

When you add a prompt to a contact flow, you can use SSML tags to provide a more personalized experience for your customers\. The default setting in a contact flow block for interpreting text to speech is **Text**\. To use SSML for text to speech in your contact flow blocks, set the **Interpret as** field to **SSML** as shown in the following image\.

![\[Image of the settings for a contact flow block showing the Text to speech Interpret as field set to SSML.\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-interpret-as-ssml.png)

The following SSML tags are supported in Amazon Connect:
+ speak
+ break
+ lang
+ mark
+ p
+ phoneme
+ prosody
+ s
+ say\-as
+ sub
+ w
+ amazon:effect name="whispered"

If you use an unsupported tag in your input text it is automatically ignored when it is processed\. To learn more about the SSML tags, see [SSML Tags in Amazon Polly](https://docs.aws.amazon.com/polly/latest/dg/supported-ssml.html)\.