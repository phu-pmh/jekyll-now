---
layout: post
title: Word2Vec : Explain like you're a Middle schooler
---

ဒီ post မှာ Deep Learning for NLP အတွက် အခြေခံအကျဆုုံးဖြစ်တဲ့ Word2Vec အကြောင်းကိုု ခက်ခက်ခဲခဲ သချင်္ာတွေ algorithm ​တွေမပါပဲ မိတ်ဆက်ပေးချင်ပါတယ်။
"Explain Like I'm 5" ပုံုစံမျိုးပေါ့။ ဒါပေမယ့် ၅နှစ်သားကိုုရှင်းပြဖိုု့က လက်ပေါက်ကတ်တာမိုု့ အလယ်တန်းကျောင်းသား တယောက်ကိုုရှင်းသလိုုရှင်းပြကြည့်ပါမယ်။

အလုုပ်မှာ ဝင်ဝင်ချင်းမှာ အထက်လူကြီးက ပထမဆုံုးဖတ်ဖိုု့ပေးတဲ့ Paper က Word2Vec အကြောင်း။ (T. Mikolov et al.) 
NUS မှာ Deep Learning for NLP class တက်တော့လဲ ပထမဦးဆုံုးသင်ရတာက Word2Vec ပဲ။
MNIST(digit recognition) က Machine Learning အတွက် Hello World ဆိုုရင် Word2vec က DeepNLP အတွက် Hello World ပဲလိုု့တောင်ပြောလိုု့ရမလား..။
NLP လုုပ်နေတဲ့သူတွေနဲ့တော့ word2vec ကရင်းနှီးပြီးသားနေမှာပါ။ မရင်းနှီးသေးတဲ့လူတွေအတွက် Word2vec ကိုုမိတ်ဆတ်ပေးချင်ပါတယ်။

ပထမဆုံုး Word2vec မပြောခင် Word Embeddings ဆိုုတာဘာလဲအရင်ပြောရအောင်။
Machine Learning Algorithm တွေအတွက် Input ပေးရင် Text တို့ Image တိုု့ကိုု ဒီအတိုုင်းထည့်လိုု့မရဘူး။ 
သူတိုု့ကိုု သချင်္ာတွက်လိုု့ရအောင် Vector form ပြောင်းပေးရတယ်။ Image ဆိုရင်တော့ Pixel တွေကိုု ဂဏန်းပြောင်းပြီး ပေးလိုုက်လိုု့ရတယ်ပေါ့။
Text ဆိုရင်ဘယ်လိုုပြောင်းမလဲ?
အဲဒီမှာ ဟိုုးအရင်တုုန်းက One-hote Vector ကိုုသုံုးကြတယ်။
 ဥပမာ ကိုုယ့် Corpus မှာ "I love delicious pizza" ဆိုုပြီး စာလုံုး ၄လုံုးရှိတယ်ထား။
Pizza အတွက် vector ကို [0 0 0 1] ဆိုပြီးထားလိုုက်တယ်။ Pizza ရဲ့ index ကိုု 1 ပေးပြီးကျန်တာကိုု 0 ပေးတာပေါ့။
တခြား အဲလိုု ပိုုပြီး advanced ဖြစ်ပေမယ့် ခပ်ဆင်ဆင်လိုု့ပြောလိုု့ရတဲ့ traditional text mining methods တွေလဲရှိတယ်။
သူတိုု့က Data Mining task တွေမှာ အသုံုးဝင်ပေမယ့် တကယ်တမ်းကျတော့ ဘာသာစကားကို နားလည်တယ်လိုု့ပြောလိုု့မရဘူး။

ဥပမာပေးရရင် ကိုုယ်က Fried Chicken နဲ့ပတ်သတ်တာကိုုရှာချင်တယ်ထား၊ သူတိုု့က Fried နဲ့ Chicken ပါတာအားလုံုး၊ ကိုုယ်မလိုုချင်တဲ့ ကြက်ထမင်းကြော် (Chicken Fried Rice) တို့ဘာတို့ကိုပါ  ရောသမမွှေပြီးပေးတယ်။ အလုပ်တော့ဖြစ်တယ် ဒါပေမယ့် ဘာသာစကားကိုု နားမလည်ဘူးပေါ့။ အဲတော့ meaning ကိုုပါ capture နိုုင်တဲ့ representation တခုုရှိရင် ပိုုကောင်းမယ်။


Word2Vec ကလွယ်ကူပေမယ့် အရမ်းအသုံုးဝင်ပြီး အံ့သြစရာကောင်းလောက်တဲ့ ရလာဒ်တွေပေးတဲ့ algorithm တခုပဲ။
ဘာလိုု့လဲဆိုုတော့ Corpus အကြီးကြီးတခုုကိုု Word2vec algorithm နဲ့ train လုပ်ပြီးရလာတဲ့ word vector တွေဟာ syntatic ကော semantic meaning ကိုပါ ဖမ်းယူထားနိုုင်တယ်။ 
ဥပမာ:  W<sub>Man</sub>  - W<sub>Woman</sub> + W<sub>King</sub>  ~= W<sub>Queen</sub> 

အဲဒီမှာ W<sub>Man</sub> ဆိုတာ Man ဆိုတဲ့စာလုံးအတွက် Word Embedding(Vector) ပေါ့။
ဆိုုလိုုရင်းကတော့ Man ထဲက Woman ကိုနှူတ်ပြီးရလာတဲ့ vector က Gender ရဲ့ semantic meaning ကို capture လုုပ်ထားနိုုင်တယ်ဆိုုတဲ့သဘောပဲ။
အဲကောင်ကိုုလွယ်လွယ်နဲ့ ဖိုု->မ Gender Vector လိုု့ခေါ်လိုုက်ရအောင်။ အဲဒီ ဖိုမ vector ကိုု ကိုုယ့် vocabulary ထဲမှာရှိတဲ့ ယောက်ျားနဲ့ဆိုုင်တဲ့ words တွေဆီသွားပေါင်းကြည့်ရင် သူနဲ့သက်ဆိုုင်တဲ့ မိန်းမ word vector ရတယ်။ King ဆီသွားပေါင်းရင် Queen ရတယ်။ 

ဒါတင်မကဘူး syntatic (grammar) meaning ကိုလဲဖမ်းယူထားနိုုင်တယ်။ 
ဥပမာ: 
apple - apples + orange ~= oranges
study - studied + work ~= worked
Syntactic structures တွေဖြစ်တဲ့ Plural တို့ Past tense တို့ကိုလဲ သူကနားလည်တယ်။

ထားပါတော့ စပိန်နိုုင်ငံရဲ့မြို့တော်ရဲ့ vector ကိုုရှာချင်ရင်.. Myanmar - Yangon + Spain ဆိုပြီးရာလိုုက်ရင် ရလာဒ်က Madrid နဲ့အနီးဆုံုးဖြစ်လိမ့်မယ်။

ကဲ... အံ့သြဖိုု့မကောင်းဘူးလား။ neural network တခုုကိုု large text corpus တခုုနဲ့ train လိုုက်တာနဲ့ မျက်လှည့်ပြသလိုုပဲ သူ ့့အလိုလို syntax and semantic meaning တွေနားလည်လာတယ်ဆိုုတာ။ (အမှန်တကယ်ကတော့ မျက်လှည့်မဟုုတ်ပါဘူး။ Linguistic နဲ့လဲဆိုုင်တယ်..။ အသေးစိတ်ရေးရင် အလယ်တန်းကျောင်းသားကိုုရှင်းပြတာနဲ့မတူတော့လိုု့ အချိန်ရမှ နောက်တပိုု့ရေးပြီးရှင်းမယ် :P )