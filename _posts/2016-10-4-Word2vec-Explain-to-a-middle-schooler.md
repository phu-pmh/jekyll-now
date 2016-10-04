---
layout: post
title: Word2Vec - Explain like you're a Middle schooler
---

ဒီ post မှာ Deep Learning for NLP အတွက် အခြေခံအကျဆုံးဖြစ်တဲ့ Word2Vec အကြောင်းကို ခက်ခက်ခဲခဲ သချင်္ာတွေ algorithm ​တွေမပါပဲ မိတ်ဆက်ပေးချင်ပါတယ်။
"Explain Like I'm 5" ပုံုစံမျိုးပေါ့။ ဒါပေမယ့် ၅နှစ်သားကိုရှင်းပြဖို့က လက်ပေါက်ကတ်တာမို့ အလယ်တန်းကျောင်းသား တယောက်ကိုရှင်းသလိုုရှင်းပြကြည့်ပါမယ်။

အလုပ်မှာ ဝင်ဝင်ချင်းမှာ အထက်လူကြီးက ပထမဆုံုးဖတ်ဖို့ပေးတဲ့ Paper က Word2Vec အကြောင်း။ (T. Mikolov et al.) 
NUS မှာ Deep Learning for NLP class တက်တော့လဲ ပထမဦးဆုံုးသင်ရတာက Word2Vec ပဲ။
MNIST(digit recognition) က Machine Learning အတွက် Hello World ဆိုရင် Word2vec က DeepNLP အတွက် Hello World ပဲလို့တောင်ပြောလိုု့ရမလား..။
NLP လုပ်နေတဲ့သူတွေနဲ့တော့ word2vec ကရင်းနှီးပြီးသားနေမှာပါ။ မရင်းနှီးသေးတဲ့လူတွေအတွက် Word2vec ကိုမိတ်ဆတ်ပေးချင်ပါတယ်။

ပထမဆုံုး Word2vec မပြောခင် Word Embeddings ဆိုတာဘာလဲအရင်ပြောရအောင်။
Machine Learning Algorithm တွေအတွက် Input ပေးရင် Text တို့ Image တို့ကို ဒီအတိုင်းထည့်လို့မရဘူး။ 
သူတို့ကို သချင်္ာတွက်လိုု့ရအောင် Vector form ပြောင်းပေးရတယ်။ Image ဆိုရင်တော့ Pixel တွေကိုု ဂဏန်းပြောင်းပြီး ပေးလိုက်လိုု့ရတယ်ပေါ့။
Text ဆိုရင်ဘယ်လိုပြောင်းမလဲ?

အဲဒီမှာ ဟိုးအရင်တုုန်းက One-hote Vector ကိုုသုံုးကြတယ်။  
ဥပမာ ကိုယ့် Corpus မှာ "I love delicious pizza" ဆိုပြီး စာလုံုး ၄လုံုးရှိတယ်ထား။  
Pizza အတွက် vector ကို [0 0 0 1] ဆိုပြီးထားလိုုက်တယ်။ Pizza ရဲ့ index ကို 1 ပေးပြီးကျန်တာကို 0 ပေးတာပေါ့။  
တခြား အဲလို ပိုပြီး advanced ဖြစ်ပေမယ့် ခပ်ဆင်ဆင်လိုု့ပြောလိုု့ရတဲ့ traditional text mining methods တွေလဲရှိတယ်။  
သူတို့က Data Mining task တွေမှာ အသုံုးဝင်ပေမယ့် တကယ်တမ်းကျတော့ ဘာသာစကားကို နားလည်တယ်လိုု့ပြောလိုု့မရဘူး။

ဥပမာပေးရရင် ကိုယ်က Fried Chicken နဲ့ပတ်သတ်တာကိုုရှာချင်တယ်ထား၊ သူတိုု့က Fried နဲ့ Chicken ပါတာအားလုံုး၊ ကိုယ်မလိုချင်တဲ့ ကြက်ထမင်းကြော် (Chicken Fried Rice) တို့ဘာတို့ကိုပါ  ရောသမမွှေပြီးပေးတယ်။ အလုပ်တော့ဖြစ်တယ် ဒါပေမယ့် ဘာသာစကားကိုု နားမလည်ဘူးပေါ့။ အဲတော့ meaning ကိုပါ capture နိုင်တဲ့ representation တခုရှိရင် ပိုကောင်းမယ်။


Word2Vec ကလွယ်ကူပေမယ့် အရမ်းအသုံုးဝင်ပြီး အံ့သြစရာကောင်းလောက်တဲ့ ရလာဒ်တွေပေးတဲ့ algorithm တခုပဲ။  
ဘာလိုု့လဲဆိုုတော့ Corpus အကြီးကြီးတခုကို Word2vec algorithm နဲ့ train လုပ်ပြီးရလာတဲ့ word vector တွေဟာ syntatic ကော semantic meaning ကိုပါ ဖမ်းယူထားနိုုင်တယ်။  

ဥပမာ:  **Man**  - **Woman** + **King**  ~= **Queen**

အဲဒီမှာ **Man** ဆိုတာ Man ဆိုတဲ့စာလုံးအတွက် Word Embedding(Vector) ပေါ့။  
ဆိုလိုရင်းကတော့ **Man** ထဲက **Woman** ကိုနှူတ်ပြီးရလာတဲ့ vector က Gender ရဲ့ semantic meaning ကို capture လုပ်ထားနိုုင်တယ်ဆိုုတဲ့သဘောပဲ။  
အဲကောင်ကိုလွယ်လွယ်နဲ့ **ဖို->မ Gender Vector** လို့ခေါ်လိုက်ရအောင်။ အဲဒီ ဖိုမ vector ကိုု ကိုုယ့် vocabulary ထဲမှာရှိတဲ့ ယောက်ျားနဲ့ဆိုုင်တဲ့ words တွေဆီသွားပေါင်းကြည့်ရင် သူနဲ့သက်ဆိုုင်တဲ့ မိန်းမ word vector ရတယ်။  
**King** ဆီသွားပေါင်းရင် **Queen** ရတယ်။ 

ဒါတင်မကဘူး syntatic (grammar) meaning ကိုလဲဖမ်းယူထားနိုုင်တယ်။  
ဥပမာ:  
- **apple - apples + orange ~= oranges**
- **study - studied + work ~= worked**  
Syntactic structures တွေဖြစ်တဲ့ Plural တို့ Past tense တို့ကိုလဲ သူကနားလည်တယ်။

ထားပါတော့ စပိန်နိုင်ငံရဲ့မြို့တော်ရဲ့ vector ကိုရှာချင်ရင်..  
**Myanmar - Yangon + Spain** ဆိုပြီးရာလိုက်ရင် ရလာဒ်က **Madrid** နဲ့အနီးဆုံုးဖြစ်လိမ့်မယ်။

![Word2Vec Visualization (Photo: Tensorflow)]({{ https://www.tensorflow.org/versions/r0.10/tutorials/word2vec/index.html }}/images/word2vec1.png)
*Word2Vec Visualization (Photo: Tensorflow)*

ကဲ... အံ့သြဖို့မကောင်းဘူးလား။ neural network တခုကို large text corpus တခုနဲ့ train လိုက်တာနဲ့ မျက်လှည့်ပြသလိုပဲ သူ ့့အလိုလို syntax and semantic meaning တွေနားလည်လာတယ်ဆိုတာ။ (အမှန်တကယ်ကတော့ မျက်လှည့်မဟုုတ်ပါဘူး။ Linguistic နဲ့လဲဆိုင်တယ်..။ အသေးစိတ်ရေးရင် အလယ်တန်းကျောင်းသားကိုုရှင်းပြတာနဲ့မတူတော့လိုု့ အချိန်ရမှ နောက်တပိုု့ရေးပြီးရှင်းမယ် :P )

PS. Pardon my bad writing. I wanted to practice technical writing in Burmese and I tried my best, but certain things are hard to translate in Burmese. 
