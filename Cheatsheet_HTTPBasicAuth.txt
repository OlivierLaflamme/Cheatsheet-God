[>] HTTP Basic Authentication Dictionary and Brute-force attacks with Burp Suite

http://www.dailysecurity.net/2013/03/22/http-basic-authentication-dictionary-and-brute-force-attacks-with-burp-suite/

Burp Suite against HTTP Basic authentication

To implement the attack you need to capture one authentication request with Burp Proxy and send it to Burp Intruder.

Mark only the Base64 encoded string and click Add button to put the markers around it.

Dictionary attack

For the dictionary attack I’m using custom iterator intruder option. It allows you to generate your own custom payload string consisting from several substrings. For every substring you could specify separator which is basically e suffix. The Intruder calls those substrings “positions”.
Following this logic in position 1 we would like to load an username followed by separator semicolumn and then load password for position 2.
Go to Payload tab and select Custom iterator option from Payload type dropdown box.
Burp Suite Custom Iterator
Select position 1 from the Position dropdown box and load your usernames list in List items for position 1 listbox. Put semicolumn in the Separator for position 1 text box.
Position 1 list and separator option
Select position 2 from the Position dropdown box and load your passwords list in List items for position 2 listbox.
Position 2
After you’ve set your two positions you need to tell the Intruder to encode the payload string using Base64 encoding. Go to Payload processing sections and click Add button. Select Payload encoding option and then Base64.
PayloadProcessin_AddRule_Encode
PayloadProcessingEncode
By default Burp Intruder URL encodes the payload. Base64 strings often contain = symbol. That is why it is a good idea to exclude it from the list of URL characters for encoding.
That’s it. You can start the Intruder attack.

Bruteforce attack

The method I’m using for the bruteforce attack is targeting only one username per Intruder attack.
Select Brute forcer from the Payload type dropdown and then set the length of the password and the characterset you would like the Intruder to use while constructing the password strings.
Burp Intruder Brute forcer
In order to specify the username you would like to brute-force you need to set Payload processing rule. Add new rule with Add prefix type and fill up the username followed by semi-column.
Burp Intruder Add Prefix
Add another rule to encode the payload using Base64. And finally remove = from the list of symbols subject of URL encoding.
Burp Sutei Bruteforce Attack Settings
Done! You can start the Intruder attack!

[>] Automated Security Analyser for ASP.NET Websites 

https://asafaweb.com