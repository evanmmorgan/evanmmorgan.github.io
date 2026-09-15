# "This isn't working"

The kinds of questions we ask can entirely determine the answer we get and the level of effort the person reading the question wants to put into responding to you. I remember a time when I was initially learning how to program and I was confused on the syntax of Java, so during one of our class recitations I had asked a TA something along the lines of “This isn’t working, what do I do”. And the TA had no idea what I was talking about besides the fact that there was code on my screen and so it took some back and forth before I actually got the answer I was looking for. 

Questions like these on online forums are exactly the reason why so many people’s questions go ignored. Eric Raymond created a guideline essay here “How To Ask Questions The Smart Way” on how to effectively ask questions in a way where people will want to respond to you. Instead of asking a broad question that didn’t require much thought, it’s better to ask a carefully thought out question with some signs that you actually did some research beforehand. 

# An example of a question that was asked in a smart way

[Smart Question](https://stackoverflow.com/questions/80002830/casting-an-out-of-range-counter-through-double-clamps-it-to-int64-max) 

```sql
A gateway import table temporarily stores counter values as strings. One device sent 9223372036854775808, which is one greater than the maximum INT64. I expected every conversion path to reject it, but an intermediate DOUBLE cast silently changes it into a valid-looking counter in Apache IoTDB 2.0.8 table model.
The reduced input is:
CREATE TABLE imported_counters ( gateway_id STRING TAG, raw_value STRING FIELD ); INSERT INTO imported_counters(time, gateway_id, raw_value) VALUES (1000, 'gw-a', '9223372036854775808');
This is the expression used by a generic numeric-normalization stage:
SELECT raw_value, CAST(CAST(raw_value AS DOUBLE) AS INT64) AS parsed_value FROM imported_counters;
Instead of reporting overflow, it returns INT64 max:
+-------------------+-------------------+ | raw_value| parsed_value| +-------------------+-------------------+ |9223372036854775808|9223372036854775807| +-------------------+-------------------+
Direct conversion of the same stored text is rejected:
SELECT raw_value, CAST(raw_value AS INT64) AS parsed_value FROM imported_counters;
Msg: org.apache.iotdb.jdbc.IoTDBSQLException: 701: Cannot cast 9223372036854775808 to INT64 type
Is the DOUBLE -> INT64 cast using a saturating conversion while STRING -> INT64 performs an overflow check? Can the two-step cast be made to fail instead of replacing an out-of-range identifier with 9223372036854775807?
```

This question is smart and it fulfills the precepts that are established by Raymond. The title states object and deviation, it reports raw output including the error string, and the closing question names exactly what kind of response the person asking this question wants. It’s clear that this person put some effort into looking up some answers before posting this question, and for this reason they quickly received some feedback:

# What the answers look like

This question was asked just a few hours ago as of the time of writing this essay. It already has received 1 reply with a solid suggestion on how to fix the person who asked’s code. 

![Answer to question](images/goodanswer.pnggoodanswer.png)//insert image here

# An example of a question that was NOT asked in a smart way

[Not smart question](https://stackoverflow.com/questions/80002798/unexpected-exit-of-echoserver-exe-from-wolfssl-running-on-windows)
```c
Unexpected exit of echoserver.exe from wolfssl running on windows - Stack Overflow 

I am trying to run the example ssh echoserver that is provided from wolfssl and wolfssh (no code change) I have echoserver.exe compiling but when running it runs but that unexpectedly exits when running, I tracked it down to WFREE call and it just simply exits there.
Running the application in debug verbosity I get the following:
2026-09-13 09:06:12 [DEBUG] Entering wolfSSH_Init() 2026-09-13 09:06:12 [DEBUG] Leaving wolfSSH_Init(), returning 0 2026-09-13 09:06:12 [DEBUG] Entering wolfSSH_CTX_new() 2026-09-13 09:06:12 [DEBUG] Entering CtxInit() 2026-09-13 09:06:12 [DEBUG] Leaving wolfSSH_CTX_new(), ctx = 0000026941916D20 2026-09-13 09:06:12 [DEBUG] Entering wolfSSH_SetKeyingCompletionCb() 2026-09-13 09:06:12 [DEBUG] Entering wolfSSH_CTX_SetBanner() 2026-09-13 09:06:12 [INFO] setting banner to: "wolfSSH Example Echo Server " 2026-09-13 09:06:12 [DEBUG] Entering wolfSSH_CTX_UsePrivateKey_buffer()
Once entered in there I tracked down the failure in the internal.c in the function
int IdentifyAsn1Key(const byte* in, word32 inSz, int isPrivate, void* heap, WS_KeySignature **pkey)
and the more specific code in this function:
/* if not returning key then free it */ if (pkey == NULL || *pkey == NULL) { wolfSSH_KEY_clean(key); WFREE(key, heap, dynType); // <---- THIS IS WHERE IT EXITS key = NULL; }
```

This question is interesting because this isn’t the worst post I saw, but I noticed it was closed because it was off topic and wasn’t related to any specific software algorithm or tool. Although the formatting of the post isn’t bad, the user here never doesn't give the build versions for wolfSSL or wolfSSH. This goes against Raymond’s precepts. They also never explicitly mentioned what they are looking to get out of posting a question on the forum, unlike the first question which was very clear. 

# How the community gave back to this post:

```c
Closed. This question is not about programming or software development. It is not currently accepting answers.

This question does not appear to be about a specific programming problem, a software algorithm, or software tools primarily used by programmers. If you believe the question would be on-topic on another Stack Exchange site, you can leave a comment to explain where the question may be able to be answered.
Closed 3 hours ago.
```

As we can see here, this question was closed shortly after it was asked. It didn’t get any replies due to the nature of the question.

Overall, my understanding of smart questions and the importance of asking them in a way that shows some level of interest has grown as of reading the essay by Eric Raymond. I can now personally see why some of my questions might not have been the best as I mentioned when I was learning Java, and why I might not have gotten the answers I needed because the questions I asked were too vague. It’s much more efficient to write a basic test case for your code and do a quick google search before sending a question that you don’t fully understand to people with busy schedules. Next time I ask a question whether it is online or in class, I’ll make sure to ask it in a way that shows I am not simply asking for an answer, but that I am also looking to see how I can improve after I get my reply. 

# Use of AI

I used Claude to help outline this essay and review drafts. The question selection, analysis and writing are my own. 
