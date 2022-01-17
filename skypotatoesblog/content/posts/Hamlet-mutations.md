---
title: "Hamlet Mutations"
date: 2022-01-17T19:58:28Z
---

I haven't updated this blog in a while. I have put Codewars katas aside for the moment as we are covering a lot each day on Northcoders. We have been introduced to TDD or Test Driven Development, using Jest to run tests on our functions as we write them, creating and passing progressively more complex tests until a final function is arrived reached. We are doing this in pairs on most days, periodically switching roles between 'driver' and 'navigator'. The driver writes the actual code; the navigator 'sets the direction' and gives pseudo-code for the driver to translate into JavaScript. There's a certain amount of 'performance anxiety' in coding in front of someone else which is soon be surmounted. I think we're all getting used to that feeling of goofiness when you're staring at your code and don't know why it isn't doing what you want. I have so far met three other virtual course-members while pairing, and all of them have seemed competent and pleasant to work with.

I have begun making a text adventure, spurred on by ideas that have come to me during the Northcoder lessons. I want to get it working as an html page, with an output terminal and input form to take commands. At the moment it is running in the debug console, and commands are entered directly into the .js file. I have the beginnings of a text parser that can take simple commands like "Look" to see your surroundings and "Look at skull" to look at the skull. I will eventually build it up with "use" command that will let you "use fish on the cat".

The theme is so far around mutating texts, so I have input the skull monologue from Hamlet and created a few functions that allow you to change the text.

'Spongify' takes the text and gives each character a 50/50 chance of being upper or lowercase. I give you Hamlet as performed by Spongebob Squarepants:

```
alas, poor yoRiCK! i KNEw him, horatiO: a fELlOW
of InFinIte jEst, OF MOst exCELLEnT FANcY: hE hAth
BORNE mE On hiS BACk A tHOUsaNd tImeS; aND now, How
AbHoRRed IN mY ImAgInATiON it IS! My gOrge rImS at
iT. HeRE huNG thosE LiPS ThAt i HAVe kISsed i kNow
NoT hOW OFt. where BE YOUr giBeS nOW? YOUR
gAmBoLS? yOuR sonGs? youR fLaSheS of MerrIMent,
ThaT werE wOnt to SEt tHe TaBLe On A RoAR? not ONE
Now, to mOck yOUR OwN grINNiNg? qUIte CHAp-FallEN?
nOw GeT you TO MY laDY's CHAMber, anD TeLL her, LET
heR paINT an iNCH ThIcK, To THiS favOur ShE Must
CoMe; mAKE Her LaUgh at That. pritheE, horatIO, tELl
ME One ThinG.
```

I also created a "ghoti" function, which uses "ghoti" as a key for translating the sounds in "fish".  F becomes gh, as in enough. I becomes O as in women. Sh becomes Ti as in motion. I also believe "ghoti" is the klingon word for "fish", and as we know, Shakespear is best read in the original klingon. Here's what happens when we run Spongy-Hamlet through ghoti:

```
Alas, poor Yorock! O knew hom, Horatoo: a ghellow
ogh onghonote jest, ogh most excellent ghancy: he hath
borne me on hos back a thousand tomes; and now, how
abhorred on my omagonatoon ot os! my gorge roms at
ot. Here hung those lops that O have kossed O know
not how oght. Where be your gobes now? your
gambols? your songs? your ghlaties ogh merroment,
that were wont to set the table on a roar? Not one
now, to mock your own gronnong? quote chap-ghallen?
Now get you to my lady's chamber, and tell her, let
her paont an onch thock, to thos ghavour tie must
come; make her laugh at that. Prothee, Horatoo, tell
me one thong.
```

After writing the ghoti function, it seemed only logical to write the fish function, which takes the letters in ghoti and returns them to fish. This is what happens when we fish the ghoti'd text:


```
Alas, piir Yirick! I knew him, Hiratii: a felliw
if infinite jest, if mist excellent fancy: he hath
birne me in his back a thiusand times; and niw, hiw
abhirred in my imaginatiin it is! my girge rims at
it. Here hung thise lips that I have kissed I kniw
nit hiw ift. Where be yiur gibes niw? yiur
gambils? yiur sings? yiur flashes if merriment,
that were wint ti set the table in a riar? Nit ine
niw, ti mick yiur iwn grinning? quite chap-fallen?
Niw get yiu ti my lady's chamber, and tell her, let
her paint an inch thick, ti this faviur she must
cime; make her lauf at that. Prithee, Hiratii, tell
me ine thing.
```

So it doesn't quite revert to the original text. It kind of gives it a Canterbury Tale vibe, I think.

So I plan to add these functions to items in the environment, so a spongify device, a ghoti and a fish will all mutate other objects in silly ways. I am reminded of the buttbuttinator filter and will build a function that does that to a text.

Anyway, for the rest of the evening I plan to relax as I will be up early for more bootcamps.