# cyber: ग्रेट वेब के ज्ञान की गणना

<p align="center">
  <img src="images/graph.png" />
</p>

## सार

एक आम सहमति जैसे की Google, Amazon या Facebook जैसे किसी भी स्वच्छंद ब्लैकबॉक्स बिचौलियों के बिना प्रमाण्‍य रूप से प्रासंगिक जवाब की कंप्यूटिंग के लिए अनुमति देता है । जैसे की सामग्री-पता करने योग्य सहकर्मी-से-सहकर्मी संचार नेटवर्क, जैसे IPFS, और Ethereum जैसे स्टेटफुल आम सहमति कंप्यूटर, समान उत्तर प्राप्त करने के लिए आवश्यक समाधान का सिर्फ एक हिस्सा प्रदान कर सकते हैं। हालांकि, उपर्युक्त कार्यान्वयनों से जुड़ी कम से कम 3 समस्याएं हैं। (क) प्रासंगिकता की व्यक्तिपरक प्रकृति । (ख) अधिक आकार के ज्ञान रेखांकन के लिए सर्वसम्मति कंप्यूटरों को स्केल करने में कठिनाई । (ग) ऐसे ज्ञान रेखांकनों के बीच गुणवत्ता की कमी । वे विभिन्न सरफेस अटैक्स, जैसे सिबिल अटैक्स, और इंटरएक्टिंग एजेंट्स के स्वार्थी व्यवहार से ग्रस्त हैं। इस दस्तावेज़ में, हम IPFS वस्तुओं के बीच प्रासंगिकता की साध्य आम सहमति कंप्यूटिंग के लिए एक प्रोटोकॉल को परिभाषित करते हैं, जो cyber\~Rank की टेंडरमिंट आम सहमति पर आधारित है, जिसकी गणना आम सहमति से GPU का उपयोग करके की जाती है। जैसा की proof-of-stake में हिस्सेदारी आम सहमति प्रारंभिक वितरण के साथ मदद नहीं करता है, हम पारिस्थितिकी और कुशल वितरण खेल के लिए डिजाइन रूपरेखा तैयार करते हैं। हमारा मानना है कि डोमेन-विशिष्ट ज्ञान आम सहमति कंप्यूटर के नेटवर्क के गठन के लिए प्रोटोकॉल की न्यूनतम वास्तुकला महत्वपूर्ण है। हमारे काम के परिणामस्वरूप, कुछ अनुप्रयोगों से पहले कभी अस्तित्व में नहीं रहा, जो उभर जाएगा। हम संभावित सुविधाओं और संभावित अनुप्रयोगों की दृष्टि के साथ इस दस्तावेज़ का विस्तार करते हैं।

## द ग्रेट वेब

इंटरनेट के मूल प्रोटोकॉल, जैसे की: TCP/IP, DNS, URL और HTTP/S वेब को एक बासी बिंदु पर ले आए हैं, जहां यह अभी तक स्थित है । उन सभी लाभों को ध्यान में रखते हुए, जो इन प्रोटोकॉल ने वेब के प्रारंभिक विकास के लिए उत्पादित किए हुए हैं, उसके साथ उन्होंने महत्वपूर्ण बाधाओं को उजागर किया है। यह वैश्विक है की, वेब एक महत्वपूर्ण संपत्ति होने की शुरुआत से ही एक वास्तविक खतरे में है। कनेक्शन की गति कम होती है जबकि नेटवर्क स्वयं सर्वव्यापी सरकारी हस्तक्षेप के कारण बढ़ता रहता है। उत्तरार्द्ध मानवाधिकारों के लिए एक संभावित खतरे के रूप में गोपनीयता चिंताओं का कारण बनता है।

इंटरनेट के रोजमर्रा के उपयोग के साथ शुरुआत में स्पष्ट नहीं होने वाली एक संपत्ति महत्वपूर्ण हो जाती है: जो है स्थायी लिंक एक्सचेंज करने की क्षमता, इस प्रकार, वे [समय बीतने के बाद नहीं टूटेंगे](https://ipfs.io/ipfs/QmNhaUrhM7KWWFzYYDBeyskBeyskoNyihrpHvUEBQnadwwPwigcN) एक समय में ISP के आर्किटेक्चर पर भरोसा, सरकारों को प्रभावी रूप से सेंसर पैकेट की अनुमति देता है। यह प्रत्येक इंजीनियर के लिए पारंपरिक वेब-स्टैक में अंतिम गिरावट है जो हमारे बच्चों के भविष्य के बारे में चिंतित है।

अन्य गुण, जो इतना महत्वपूर्ण नहीं हो सकता है, लेकिन बहुत वांछनीय हैं: जो है ऑफ़लाइन और वास्तविक समय कनेक्शन। औसत इंटरनेट उपयोगकर्ता के लिए, जब ऑफ़लाइन हो, तब भी उस स्थिति में भी साथ काम करने की क्षमता होनी चाहिए जो वे पहले से ही चल रहा था। एक कनेक्शन प्राप्त करने के बाद उन्हें वैश्विक स्थिति के साथ sync करने और वास्तविक समय में अपने स्वयं के अवस्था की वैधता को सत्यापित करने में सक्षम होना चाहिए। वर्तमान में, इन गुणों को आवेदन स्तर पर पेश किया जा रहा है। हमारा मानना है कि इस अधिकार को निचले स्तर के प्रोटोकॉल में एकीकृत किया जाना चाहिए।

आपात स्थिति की [एक ब्रांड-नई वेब-स्टैक](https://ipfs.io/ipfs/Qmf2rKkDPSsvdudwSmdDPbZuYae8XRV26c1wAFvv88hhw) का उद्भव एक श्रेष्ठ इंटरनेट का अवसर बनाता है। समुदाय इसे web3 कहता है। हम इसे ग्रेट वेब कहते हैं। हमारा मानना है कि विभिन्न प्रकार के निम्न-स्तरीय संचार अपरिवर्तनीय होने चाहिए और दशकों तक नहीं बदलना चाहिए, जैसे की: अपरिवर्तनीय सामग्री लिंक। वे पारंपरिक प्रोटोकॉल स्टैक की समस्याओं को दूर करने में बहुत आशाजनक लगते हैं। वे अधिक गति जोड़ते हैं और नए वेब के लिए अधिक सुलभ कनेक्शन प्रदान करते हैं। हालांकि, जैसा किसी भी अवधारणा के साथ होता है जो कुछ अद्वितीय प्रदान करता है - नई समस्याएं सामने आती हैं। इस तरह की चिंता एक सामान्य प्रयोजन खोज है। मौजूदा सामान्य-उद्देश्य वाले खोज इंजन प्रतिबंधात्मक और केंद्रीकृत डेटाबेस हैं जिन पर हर कोई भरोसा करने के लिए मजबूर है। उन खोज इंजनों को मुख्य रूप से TCP/IP, DNS, URL और HTTP/S पर आधारित क्लाइंट-सर्वर आर्किटेक्चर के लिए डिज़ाइन किया गया था। ग्रेट वेब एक चुनौती और खोज इंजन के लिए एक अवसर बनाता है जो उभरती प्रौद्योगिकियों पर आधारित है और इन उद्देश्यों के लिए विशेष रूप से डिज़ाइन किया गया है। हैरानी की बात है, अनुमतिहीन ब्लॉकचेन आर्किटेक्चर पिछले आर्किटेक्चर के लिए दुर्गम तरीके से एक सामान्य-उद्देश्य वाले खोज इंजन के निर्माण की अनुमति देता है।

## प्रतिकूल उदाहरणों की समस्या पर

[खोज इंजनों की वर्तमान आर्किटेक्चर](https://ipfs.io/ipfs/QmeS4LjoL1iMNRGuyYSx78RAtubTT2bioSGnsvoaupcHR6) एक ऐसी प्रणाली है, जिसकी इकाई सभी गंदगी को संसाधित करती है। यह दृष्टिकोण एक चुनौतीपूर्ण और एक अलग समस्या से ग्रस्त है, जो अभी तक हल किया जाना है, यहां तक कि शानदार Google वैज्ञानिकों द्वारा भी: [प्रतिकूल परिस्थितियों की समस्या](https://ipfs.io/ipfs/QmNrAFz34SLqkzhng4wAYYJeokfJU5BEBEkT4hPRi226y9y9)। Google जो समस्या स्वीकार करता है, वह यह है कि यह एल्गोरिदमिक रूप से कठिन है कि कोई विशेष नमूना प्रतिकूल है आप चाहे या नहीं यह इस बात पर असंगत है कि अपने आप में शिक्षित तकनीक कितनी भयानक है। एक क्रिप्टो-किफायती दृष्टिकोण खेल में लाभार्थियों को बदल सकता है। नतीजतन, इस दृष्टिकोण को प्रभावी रूप से संभावित सिबिल अटैक वैक्टर को हटा दिया जाएगा। यह एकल इकाई द्वारा हार्ड-कोड मॉडल क्रॉलिंग और अर्थ निष्कर्षण की आवश्यकता को हटा देता है। इसके बजाय, यह पूरी दुनिया को यह शक्ति देता है। सीखने वाला सिबिल-रेसिस्टेंट, एजेंट-जनरेटेड मॉडल, संभवतः परिमाण के आदेशों का नेतृत्व करेगा और अधिक पूर्वानुमान परिणाम देगा।

## Cyber प्रोटोकॉल

इसके मूल में प्रोटोकॉल बहुत न्यूनतर है और इसे निम्न चरणों के साथ व्यक्त किया जा सकता है:

1. परिभाषित वितरण के आधार पर cyber प्रोटोकॉल की उत्पत्ति की गणना करें
2. [ज्ञान ग्राफ](#knowledge-graph) की स्थिति को परिभाषित करें
3. एक [सर्वसम्मति कंप्यूटर](#the-notion-of-a-consensus-computer) का उपयोग करके ट्रांसक्शन इकट्ठा करें
4. सिग्नेचर की वैधता की जाँच करें
5. [बैंडविड्थ सीमा](#relevance-machine) जांचें
6. CID की वैधता की जाँच करें
7. यदि सिग्नेचर, बैंडविड्थ सीमा और CID सभी मान्य हैं, तो [cyberlinks](#cyberlinks) और लेनदेन लागू करें
8. [ज्ञान ग्राफ](#knowledge-graph) पर CID के हर दौर के लिए [cyber\~Rank](#cyberrank) के महत्व की गणना करें।

इस दस्तावेज़ के बाकी हिस्से में प्रस्तावित प्रोटोकॉल के औचित्य और तकनीकी विवरणों पर चर्चा की गई है।

## ज्ञान का ग्राफ

हम सामग्री पतों के बीच निर्देशित लिंक के भारित ग्राफ के रूप में एक ज्ञान ग्राफ का प्रतिनिधित्व करते हैं। उर्फ, सामग्री पहचानकर्ता, CID, IPFS हैश, या बस - IPFS लिंक। इस दस्तावेज़ में, हम उपर्युक्त शब्दों को समानार्थक शब्द के रूप में उपयोग करेंगे।

<p align="center">
  <img src="images/knowledge-graph.png" />
</p>

सामग्री पते अनिवार्य रूप से web3 लिंक हैं। अस्पष्ट और परस्पर उपयोग करने के बजाय:     

`https://github.com/cosmos/cosmos/blob/master/WHITEPAPER.md`

हम स्वयं वस्तु का उपयोग करते हैं:

`Qme4z71Zea9xaXScUi6pbsuTKCCNFp5TAv8W5tjdfH7yuH`

हमारे द्वारा प्राप्त ज्ञान के अनुसार ग्राफ को बनाने के लिए सामग्री पतों का उपयोग किया [यह बहुत आवश्यक है](https://steemit.com/web3/@hipster/an-idea-of-decentralized-search-for-web3-ce860b61defe5est)[IPFS](https://ipfs.io/ipfs/QmV9tSDx9UiPeWExXEeH6aoDvmihvx6jD5eLb4jbTaKGps) - [जैसे](https://ipfs.io/ipfs/QmXHGmfo4sjdHVW2MAxczAfs44RCpSeva2an4QvkzqYgfR) P2P प्रोटोकॉल के सुपरपावर जो एक खोज इंजन के लिए वांछित हैं:

- मेष-नेटवर्क फ्यूचर-प्रूफ 
- अंतर्वैयक्तिक अभिगम्यता
- सेंसरशिप प्रतिरोध
- तकनीकी स्वतंत्रता

हमारे ज्ञान का ग्राफ भयावह उस्ताद द्वारा उत्पन्न होता है। उस्ताद एकल लेन-देन, साइबरलिंक की मदद से खुद को ज्ञान ग्राफ में जोड़ते हैं। जिससे, वे अपनी सार्वजनिक कुंजियों के सामग्री पतों के लिए अपने निजी कुंजी के अस्तित्व को साबित करते हैं। इन यांत्रिकी का उपयोग करके, एक [सर्वसम्मति कंप्यूटर](#the-notion-of-a-consensus-computer) ज्ञान ग्राफ पर विषयों और वस्तुओं के बीच भिन्न भिन्नता को प्राप्त कर सकता है।

[go-cyber](https://github.com/cybercongress/go-cyber) के हमारे कार्यान्वयन [cosmos-SDK](https://github.com/cosmos/cosmos-sdk) पर आधारित है सामग्री पते पहचान और [CIDv0/CIDv1]( https://github.com/multiformats/cid#cidv0) पर आधारित है 

उस्ताद [सायबरलिंक](#cyberlinks) लगाकर ज्ञान का ग्राफ बनाते हैं।

## साइबरलिंक्स 

हमें साइबरलिंक्स का कार्य समझने के लिए एक URL लिंक (उर्फ, हाइपरलिंक) और एक IPFS लिंक के बीच अंतर को समझना होगा। एक URL लिंक सामग्री के स्थान को इंगित करता है, चाहे एक IPFS लिंक सामग्री को इंगित करता हो। स्थान लिंक और सामग्री लिंक के आधार पर वेब आर्किटेक्चर के बीच अंतर कट्टरपंथी है और इसके लिए एक अद्वितीय दृष्टिकोण की आवश्यकता होती है।

साइबरलिंक दो सामग्री पते, या IPFS लिंक, शब्दार्थ लिंक करने के लिए एक दृष्टिकोण है:

````bash
.md syntax: [QmdvsvrVqdkzx8HnowpXGLi88tXZDsoNrGhGvPvHBQB6sH](Qme4z71Zea9xaXScUi6pbsuTKCCNFp5TAv8W5tjdfH7yuH)    
.dura syntax: QmdvsvrVqdkzx8HnowpXGLi88tXZDsoNrGhGvPvHBQB6sH.Qme4z71Zea9xaXScUi6pbsuTKCCNFp5TAv8W5tjdfH7yuH
````

ऊपर दिए गए साइबरलिंक का मतलब है कि [cyber0n](https://etherscan.io/token/0x61BB10310377BB11Fff8aF5Ac5Dc8f37C628efb1E) के दौरान [go-cyber](https://github.com/cybercongress/go-cyber) की प्रस्तुति  Cosmos श्वेतपत्र के संदर्भ से होगा। साइबरलिंक्स की अवधारणा किसी भी P2P नेटवर्क में संचार प्रारूप के सरल शब्दार्थ के आसपास एक सम्मेलन है:

<p align="center">
  <img src="images/cyberlink.png" />
</p>

हम देखते हैं कि दो लिंक के बीच एक साइबरलिंक एक लिंक का प्रतिनिधित्व करना बहुत आसान है!

साइबरलिंक एक सरल, अभी तक ब्रह्मांड का एक भविष्य कहनेवाला मॉडल बनाने के लिए एक शक्तिशाली अर्थ निर्माण है। इसका मतलब यह है कि हाइपरलिंक्स के बजाय साइबरलिंक्स का उपयोग हमें उन सुपरपावर के साथ प्रदान करेंगे जो सामान्य-उद्देश्य वाले खोज इंजन के पिछले आर्किटेक्चर के लिए दुर्गम थे।

साइबरलिंक को बढ़ाया जा सकता है, अर्थात अगर दो या दो से अधिक साइबरलिंक एक उस्ताद से उप-लिंक करते हैं, तो वे लिंकचैन बना सकते हैं, जहां पहले साइबरलिंक में दूसरा लिंक दूसरे साइबरलिंक में पहले लिंक के बराबर होगा:

<p align="center">
  <img src="images/linkchain.png" />
</p>

यदि एजेंट, मूल रूप से कुछ धनवानों के साथ मूल IPFS लिंक का विस्तार करते हैं, उदाहरण के लिए, [dura](https://github.com/cybercongress/cyb/blob/dev/docs/dura.md) लिंक के साथ, तो निष्पादन नियमों पर आम सहमति एक विशिष्ट कार्यक्रम को और अधिक प्राकृतिक दृष्टिकोण में पहुँचा जा सकता है।

[go-cyber](https://github.com/cybercongress/go-cyber) साइबरलिंक्स का कार्यान्वयन हमारे प्रायोगिक web3 ब्राउज़र [cyb](https://cyb.ai), या [cyber.page](http://cyber.page) पर उपलब्ध है।

उस्ताद द्वारा प्रस्तुत साइबरलिंक को [RFC-6962 मानक](https://ipfs.io/ipfs/QmZpJLmc3T2L1FLUxzv3b8P8MBCPe15fEmUyVS7Bz8ZKMHGG) के अनुसार एक मर्कल ट्री में संग्रहित किया गया है। यह [प्रमाण-की-प्रासंगिकता](#proof-of-relevance) के लिए प्रमाणीकरण सक्षम है।

<p align="center">
  <img src="images/graph-tree.png" />
</p>

साइबरलिंक्स का उपयोग करके, हम [ज्ञान ग्राफ](#knowledge-graph) पर विषयों और वस्तुओं की प्रासंगिकता की गणना कर सकते हैं। लेकिन हमें एक [सर्वसम्मति संगणक](#the-notion-of-a-consensus-computer) की आवश्यकता है।

## एक आम सहमति कंप्यूटर की धारणा

एक आम सहमति कंप्यूटर एक अमूर्त कंप्यूटिंग मशीन है जो एजेंटों के बीच बातचीत से निकलती है। एक सर्वसम्मत कंप्यूटर में मौलिक कंप्यूटिंग संसाधनों के संदर्भ में क्षमता होती है: स्मृति और संगणना की। एजेंटों के साथ बातचीत करने के लिए कंप्यूटर को बैंडविड्थ की आवश्यकता होती है। एक आदर्श आम सहमति वाला कंप्यूटर एक कंप्यूटर है जहां:

`स्मृति का योग और संगणना सभी व्यक्तियों के लिए उपलब्ध हो`     
`इसके बराबर हो`    
`स्मृति का योग और संगणना सभी सत्यापित सर्वसम्मति कंप्यूटर के लिए उपलब्ध हो`    


हम जानते हैं कि:

`कम्प्यूटेशन की सत्यापन  < (कम्प्यूटेशन + कम्प्यूटेशन की सत्यापन)`    

Hence, we will never be able to achieve an ideal consensus computer. The CAP theorem and the scalability trilemma append more proof to this statement.

<p align="center">
  <img src="images/consensus-computer.png" />
</p>

सर्वसम्मति कंप्यूटर में 6 साल निवेश करने के बाद, हमें पता चला है कि [टेंडरमिंट](https://ipfs.io/ipfs/QmaMtD7xDgghqgjN62zWZ5TBGFiEGQtuZBjJ9sMh816KJ) आम सहमति से हमारे कार्य के लिए आवश्यक उदासीनता और इसके उत्पादन के लिए तत्परता के बीच एक अच्छा पर्याप्त संतुलन है। इसलिए, हमने टेंडरमिंट सर्वसम्मति का उपयोग करते हुए [cyber](#cyber-protocol) प्रोटोकॉल को लागू करने का फैसला किया है, जिसमें Cosmos Hub के बहुत करीब समायोजन हैं। [go-cyber](https://github.com/cybercongress/go-cyber) कार्यान्वयन 64-बाइट स्ट्रिंग-स्पेस के लिए प्रासंगिकता का 64-बिट टेंडरमिंट सर्वसम्मति कंप्यूटर है। यह अब तक आदर्श नहीं है, कम से कम 1/146 के रूप में, क्योंकि हमारे पास 146 सत्यापनकर्ता हैं जो [ज्ञान-ग्राफ] (#knowledge-graph) का निर्माण करने वाले समान संगणनाओं का सत्यापन करते हैं।

हमें संगणना, संगणना और बैंडविड्थ कंप्यूटर की बैंडविड्थ आपूर्ति को प्रश्नों की अधिकतम मांग से बांधना चाहिए। एक बुनियादी [प्रासंगिकता मशीन](#relevance-machine) के मामले में संगणना और भंडारण, बैंडविड्थ के आधार पर आसानी से भविष्यवाणी की जा सकती है। लेकिन बैंडविड्थ के लिए एक सीमित तंत्र की आवश्यकता होती है।

## प्रासंगिकता मशीन

हम एक प्रासंगिक मशीन को एक ऐसी मशीन के रूप में परिभाषित करते हैं, जो कि [ज्ञान-ग्राफ](#knowledge-graph) को पढ़ाने और अध्ययन करने के इच्छुक एजेंटों की इच्छा के आधार पर एक [ज्ञान-ग्राफ](#knowledge-graph) की स्थिति को परिवर्तित करती है। । वसीयत में हर [साइबरलिंक्स](#cyberlinks) एक मास्टर द्वारा अनुमानित किया जाता है।  जितने अधिक एजेंट [ज्ञान-ग्राफ](#knowledge-graph) की जांच करते हैं, उतना ही अधिक मूल्यवान ज्ञान बनता है। इन अनुमानों के आधार पर, सामग्री पतों के बीच प्रासंगिकता की गणना की जा सकती है। प्रासंगिकता मशीन खोज तंत्र के लिए एक सरल निर्माण को क्वेरी और उत्तर देने के माध्यम से सक्षम करती है।

प्रासंगिकता मशीन की एक गुण महत्वपूर्ण है। इसमें आगमनात्मक तर्क गुण होने चाहिए या ब्लैकबॉक्स सिद्धांत का पालन करना चाहिए:

`मशीन को वस्तुओं के बारे में किसी भी ज्ञान के बिना भविष्यवाणियों के साथ हस्तक्षेप करने में सक्षम होना चाहिए,`   
`सिवाय इसके कि कौन, कब और क्या साइबरलिंक्ड था`   

यदि हम मानते हैं कि एक [सर्वसम्मति कंप्यूटर](#the-notion-of-a-consensus-computer) लिंक किए गए वस्तुओं के बारे में कुछ जानकारी होनी चाहिए, तो ऐसे मॉडल की जटिलता अप्रत्याशित रूप से बढ़ेगी। इसलिए स्मृति और अभिकलन के लिए प्रसंस्करण कंप्यूटर की उच्च आवश्यकताएं हैं। एक प्रासंगिकता मशीन को संबोधित करने वाली सामग्री के लिए धन्यवाद जो ब्लैकबॉक्स सिद्धांत का अनुसरण करता है, उसे डेटा संग्रहीत करने की आवश्यकता नहीं है। लेकिन, फिर भी इसके शीर्ष पर प्रभावी ढंग से काम कर सकता है। एक [सर्वसम्मति कंप्यूटर](#the-notion-of-a-consensus-computer) के अंदर अर्थ की कटौती महंगा है। इसलिए, ऐसा डिज़ाइन अनुमान पर निर्भर कर सकता है। [सर्वसम्मति कंप्यूटर](#the-notion-of-a-consensus-computer) के अंदर के अर्थ को घटाने के बजाय, हमने एक प्रणाली तैयार की है जिसमें अर्थ निष्कर्षण को प्रोत्साहित किया जाता है। यह उस्ताद को अपनी इच्छा व्यक्त करने के लिए [CYB](#cyb) टोकन की आवश्यकता के कारण हासिल होता है, जिसके आधार पर, प्रासंगिकता मशीन रैंक की गणना कर सकती है।

स्पैम प्रोटेक्शन सिस्टम के केंद्र में एक धारणा है कि लेखन कार्यों को केवल उन लोगों द्वारा निष्पादित किया जा सकता है, जिनके पास प्रासंगिकता मशीन की विकासवादी सफलता में निहित स्वार्थ है। [सर्वसम्मति कंप्यूटर](#the-notion-of-a-consensus-computer) के भीतर प्रभावी हिस्सेदारी का प्रत्येक 1%  संभावित नेटवर्क बैंडविड्थ की 1%  का कंप्यूटिंग क्षमताओं का उपयोग करने की क्षमता देता है। एक सरल नियम एजेंटों से दुर्व्यवहार को रोकता है: सामग्री पहचानकर्ताओं की एक जोड़ी को केवल एक बार एक पते से साइबरलिंक किया जा सकता है।

<p align="center">
  <img src="images/algo1.png" />
</p>

किसी खाते की प्रभावी हिस्सेदारी (सक्रिय हिस्सेदारी + बंधी हुई हिस्सेदारी) को बदलने के केवल दो तरीके हैं: सीधा टोकन ट्रांसफर और बंधन संचालन।

[Cyber](#cyber-protocol) एक बहुत ही सरल बैंडविड्थ मॉडल का उपयोग करता है। इस मॉडल का मुख्य लक्ष्य किसी दिए गए स्थिरांक को दैनिक नेटवर्क विकास को कम करना है। यह किसी भी भविष्य के निवेश को बुनियादी ढांचे में पूर्वानुमान करने की क्षमता के साथ नायकों (सत्यापनकर्ताओं) को समायोजित करने के लिए किया जायेगा। इस प्रकार, यहाँ हम 'watts' या 'W' का परिचय देते हैं। प्रत्येक संदेश प्रकार में एक निर्दिष्ट W लागत होती है। निरंतर 'DesirableBandwidth', W मूल्य द्वारा खर्च किए जाने योग्य वांछनीय 'RecoveryWindow' को निर्धारित करता है। पुनर्प्राप्ति अवधि परिभाषित करती है कि एक उस्ताद 0 से अधिकतम बैंडविड्थ तक कितनी तेजी से अपने बैंडविड्थ को पुनर्प्राप्त कर सकता है। एक उस्ताद के पास अपनी प्रभावी हिस्सेदारी के लिए अधिकतम W आनुपातिक है, जो निम्न सूत्र द्वारा निर्धारित किया गया है:

`AgentMaxW = EffectiveStake * DesirableBandwidth`

The period 'AdjustPricePeriod' sums up how much W was spent during the period 'RecoveryPeriod' in the latest block. 'SpentBandwidth' / 'DesirableBandwidths' ratio is called the fractional reserve ratio. When network usage is low, the fractional reserve ratio adjusts the message cost to allow masters with a lower stake to commit more transactions. When the demand for resources increases, the fractional reserve ratio goes > 1, consequently, increasing message cost and limiting final tx count for a long-term period (W recovery will be < then W spending). As no one uses all of their possessed bandwidth, we can safely use up to 100x fractional reserves within a price recalculation target period. Such mechanics provide a discount for creating [cyberlinking](#cyberlinks), thus, effectively maximizing demand for it. You can see that the proposed design needs demand for full bandwidth for the relevance to become valuable.

Human intelligence is organized in such a manner that none-relevant and none-important memories are forgotten over time. The same can be applied to the relevance machine. The relevance machine can implement [aggressive pruning strategies](https://ipfs.io/ipfs/QmP81EcuNDZHQutvdcDjbQEqiTYUzU315aYaTyrVj6gtJb), such as, the pruning of the history of the formation of the [knowledge-graph](#knowledge-graph), or forgetting links that become less relevant.

As a result, the implemented cybernomics of [CYB](#cyb) tokens serves not just as will-expression and spam-protection mechanisms, but also, functions as an economics regulation tool that can align the processing capacity of heroes and the market demand for processing. The go-cyber implementation of the relevance machine is based on a very straightforward mechanism, called: cyber\~Rank.

## cyber\~Rank

Ranking using a [consensus computer](#the-notion-of-a-consensus-computer) can be challenging, as consensus computers have serious resource constraints. First, we must ask ourselves: why do we need to compute and to store the rank on-chain and not follow the same way as [Colony](https://ipfs.io/ipfs/QmZo7eY5UdJYotf3Z9GNVBGLjkCnE1j2fMdW2PgGCmvGPj) or [Truebit](https://ipfs.io/ipfs/QmTrxXp2xhB2zWGxhNoLgsztevqKLwpy5HwKjLjzFa7rnD)?

When rank was computed inside a [consensus computer](#the-notion-of-a-consensus-computer) one has easy access to the content distribution of that rank and an easy way to [build provable applications](#apps) on top of that rank. Hence, we have decided to follow a more cosmic architecture. In the next section we describe the [proof of relevance](#proof-of-relevance) mechanism, which allows the network to scale with the help of domain-specific [relevance machines](#relevance-machine). Those work concurrently, thanks to the IBC protocol.

Eventually, the [relevance machine](#relevance-machine) needs to obtain (1) a deterministic algorithm, that will allow for the computation of the rank on a continuously appending network, which itself, can scale to the orders of magnitude of the likes of [Google](https://google.com). Additionally, a perfect algorithm (2) must have linear memory and computational complexity. Most importantly, it must have (3) the highest provable prediction capabilities for the existence of relevant [cyberlinks](#cyberlinks).

After [thorough research](https://ipfs.io/ipfs/QmTJPJ55ePgR2MS1HoAtyqS1mteVLXUjAS4H8W97EEopxC), we have found that it is impossible to obtain the silver bullet. Therefore, we have decided to find a more basic, bulletproof way, that can bootstrap the network: [the rank](http://ipfs.io/ipfs/QmbuE2Pfcsiji1g9kzmmsCnptqPEn3BuN3BhnZHrPVsiVw) which Larry and Sergey used to bootstrap their previous network. The key problem with the original PageRank is that it wasn't resistant to sybil attacks. However, a token-weighted PageRank which is limited by a token-weighted bandwidth model does not inherit the key problem of the naive PageRank, because - it is resistant to sybil attacks. For the time being, we will call it cyber\~Rank, until something more suitable will emerge. The following algorithm is applied to its implementation at Genesis:

<p align="center">
  <img src="images/algo2.png" />
</p>

We understand that the ranking mechanism will always remain a red herring. This is why we expect to rely on the on-chain governance tools that can define the most suited mechanism at a given time. We suppose that the network can switch from one algorithm to another, not simply based on subjective opinion, but rather on economical a/b testing through 'hard spooning' of domain-specific [relevance machines](#relevance-machine).

cyber\~Rank दो डिजाइन निर्णय लेता है जो सर्वोपरि हैं: (1) यह एजेंटों के वर्तमान इरादे के लिए खाता है, और (2) यह रैंक की मुद्रास्फीति को प्रोत्साहित करता है [सायबरलिंक्स](#cyberlinks) पहला गुण यह सुनिश्चित करता है कि cyber\~Rank के साथ बाजी नहीं उठाया जा सकता है। यदि कोई एजेंट अपने खाते से अपने [CYB](#cyb) टोकन को स्थानांतरित करने का निर्णय लेता है, तो [प्रासंगिकता मशीन] (#relevance-machine) चालू इरादों के अनुसार एजेंट के खाते से संबंधित सभी [सायबरलिंक्स](#cyberlinks) को समायोजित कर देगा। और इसके विपरीत, अगर कोई एजेंट अपने खाते में [CYB](#cyb) टोकन स्थानांतरित करता है, तो इस खाते से जमा किए गए सभी [सायबरलिंक्स](#cyberlinks) तुरंत अधिक प्रासंगिकता प्राप्त करेंगे। अतीत में पुख्ता नहीं होने के लिए दूसरी संपत्ति आवश्यक है। जैसे ही नए [सायबरलिंक्स](#cyberlinks) लगातार जोड़े जाते हैं, वे आनुपातिक रूप से पहले से मौजूद लिंक की रैंक को फीका कर देंगे। यह गुण एक ऐसी स्थिति को रोकती है, जहां नई और बेहतर सामग्री की निम्न रैंक होती है, क्योंकि यह हाल ही में प्रस्तुत की गई थी। हम उम्मीद करते हैं कि ये निर्णय [ज्ञान ग्राफ](#knowledge-graph) की लंबी श्रृंखला में हाल ही में जोड़ी गई सामग्री के लिए एक अंतर्ग्रहण गुणवत्ता को सक्षम करने के लिए।

हम वोट-खरीद की समस्या पर चर्चा करना पसंद करेंगे। एक घटना के रूप में वोट खरीदना बुरा नहीं है। वोट-खरीद के साथ दुविधाएं उन प्रणालियों के भीतर दिखाई देती हैं जहां मतदान उस सिस्टम मुद्रास्फीति के आवंटन को प्रभावित करता है। उदाहरण के लिए, [Steem](http://ipfs.io/ipfs/QmepU77tqMAHHuiSASUvUnu8f8ENuPF2Kfs97WjLn8vAS3) या कोई भी स्टेट-आधारित प्रणाली। वोट-खरीदना एक प्रतिकूल के लिए आसानी से लाभदायक हो सकता है जो मूल्य जोड़ने के लिए आवश्यकता के बिना शून्य-राशि के खेल को नियुक्त करता हो। विकेंद्रीकृत खोज का हमारा मूल विचार इसी दृष्टिकोण पर आधारित था। लेकिन, हमने उस विचार को अस्वीकार कर दिया है, जिससे [ज्ञान ग्राफ](#knowledge-graph) के गठन का प्रोत्साहन सर्वसम्मति के स्तर तक पहुंच गया। वातावरण में जहां प्रत्येक प्रतिभागी को भविष्य कहनेवाला मॉडल को प्रभावित करने के लिए सिस्टम में कुछ मूल्य लाना होगा, वोट खरीदना एनपी-कठिन समस्या बन जाती है। इसलिए, सिस्टम के लिए फायदेमंद हो जाता है।

[प्रासंगिकता मशीन](#relevance-machine) का वर्तमान कार्यान्वयन रैंक की गणना करने के लिए GPU का उपयोग करता है। मशीन 64-बाइट CID स्पेस में किसी भी खोज अनुरोध के लिए प्रासंगिक परिणामों का जवाब और वितरण कर सकती है। हालाँकि, यह डोमेन-विशिष्ट [प्रासंगिकता मशीनों](#relevance-machine) के नेटवर्क का निर्माण करने के लिए पर्याप्त नहीं है। [सर्वसम्मति संगणक](#the-notion-of-a-consensus-computer) एक दूसरे के लिए प्रासंगिकता सिद्ध करने की क्षमता होनी चाहिए।

## प्रासंगिकता का प्रमाण

हमने नेटवर्क को इस धारणा के तहत डिजाइन किया है कि खोज के संबंध में, इस तरह के दुर्भावनापूर्ण व्यवहार के रूप में मौजूद नहीं है। यह माना जा सकता है कि जवाब खोजने के इरादे से कोई दुर्भावनापूर्ण व्यवहार नहीं किया जा सकता है। यह दृष्टिकोण किसी भी सतह के हमलों को काफी कम करता है।

````bash
इस तथ्य के आधार पर रैंकों की गणना की जाती है कि कुछ खोजा गया था, इस प्रकार जुड़ा हुआ था, और परिणामस्वरूप - पूर्वानुमानित मॉडल को प्रभावित किया जा सके।
````

क्वांटम यांत्रिकी में एक अच्छा सादृश्य देखा जाता है, जहां अवलोकन स्वयं व्यवहार को प्रभावित करता है। यही कारण है कि हमें नकारात्मक मतदान जैसी किसी चीज की कोई आवश्यकता नहीं है। ऐसा करने से, हम सब्जेक्टिविटी को प्रोटोकॉल से निकाल देते हैं और हम प्रासंगिकता के प्रमाण को परिभाषित कर सकते हैं।

<p align="center">
  <img src="images/graph-tree.png" />
</p>

प्रत्येक नए CID को एक अनुक्रम संख्या प्राप्त होती है। संख्या शून्य से शुरू होती है। फिर प्रत्येक नए CID के लिए एक के बाद एक वृद्धि। इसलिए, हम रैंक को एक-आयामी सरणी में स्टोर कर सकते हैं, जहां सूचकांक CID अनुक्रम संख्या हैं। मर्कल ट्री की गणना [RFC-6962 मानक](https://ipfs.io/ipfs/QmZpJLmc3T2L1FLUxzvU3P8MBCPe15fEUUVV77zzZZMMGG) पर आधारित है। मर्कल ट्री का उपयोग करते हुए, हम किसी भी दिए गए सामग्री पते के लिए रैंक का प्रभावी रूप से प्रमाण कर सकते हैं। जबकि प्रासंगिकता अभी भी स्वभाव से व्यक्तिपरक है, हमारे पास एक सामूहिक प्रमाण है कि कुछ समय में कुछ समुदाय के लिए प्रासंगिक था।

इस प्रकार के प्रमाण किसी भी दो [IBC संगत](https://ipfs.io/ipfs/QmSGbrGAPZtR6Q1jHe8mmS3bLBehKmfp9ZYvYg5ycaZuk) [सर्वसम्मति कंप्यूटर](#the-notion-of-a-consensus-computer) का उपयोग करके कंप्यूटर को साबित कर सकते हैं। इसका अर्थ है कि डोमेन-विशिष्ट [प्रासंगिकता मशीनें](#relevance-machine) फल-फूल सकती हैं।

एक सामान्य [go-cyber](https://github.com/cybercongress/go-cyber) कार्यान्वयन के लिए प्रासंगिकता में, मर्कले ट्री की गणना हर दौर में की जाती है और इसकी जड़ हैश ABCI के लिए प्रतिबद्ध है।

## गति

हमें पारंपरिक वेब-एप्लिकेशन की भावना के साथ उपयोगकर्ताओं को प्रदान करने के लिए तत्काल पुष्टि समय की आवश्यकता है। यह एक शक्तिशाली वास्तुशिल्प आवश्यकता है जो किफायती टोपोलॉजी और [cyber](#cyber-protocol) प्रोटोकॉल की मापनीयता को आकार देती है। प्रस्तावित ब्लॉकचेन डिज़ाइन [टेंडरमिंट सर्वसम्मति](https://ipfs.io/ipfs/QmaMtD7xDgghqgNN62zWZ5TBGFiEjGQtuGujj9sMh816KJ) पर आधारित है, जिसमें 146 सत्यापनकर्ताओं के साथ एल्गोरिथ्म है और इसमें त्वरित, 5 सेकंड tx अंतिम समय है। औसत पुष्टिकरण समय 1 सेकंड के करीब है और जटिल ब्लॉकचेन इंटरैक्शन को एजेंटों के लिए लगभग अदृश्य बना देता है।

हम गति - रैंक गणना के संदर्भ में एक विशेष [go-cyber](https://github.com/cybercongress/go-cyber) संपत्ति को निरूपित करते हैं। सर्वसम्मति का हिस्सा होने के नाते, यह दौर के भीतर ट्रांसैक्शन सत्यापन के समानांतर होता है। एक दौर हितधारकों द्वारा परिभाषित एक सर्वसम्मति चर है। स्थापना के समय, एक राउंड को 20 ब्लॉक पर सेट किया जाता है। व्यावहारिक रूप से, यह इंगित करता है कि हर 100 सेकंड पर नेटवर्क को [ज्ञान ग्राफ](#knowledge-graph) के वर्तमान रूट हैश पर सहमत होना चाहिए। इसका अर्थ यह है कि प्रस्तुत किया गया हर [साइबरबरलिंक](#cyberlinks) [ज्ञान ग्राफ] (#knowledge-graph) का एक हिस्सा बन जाता है और लगभग 50 सेकंड की औसत अवधि के भीतर एक रैंक प्राप्त करता है। [Google](https://google.com) रैंक के शुरुआती दिनों में हर हफ्ते मोटे तौर पर फिर से काम शुरू कर दिया गया था। हम मानते हैं कि ग्रेट वेब के स्वामी वास्तविक समय में रैंकिंग में परिवर्तन को देखकर प्रसन्न होंगे, लेकिन, इस धारणा के साथ नेटवर्क लॉन्च करने का फैसला किया है कि यह विंडो पर्याप्त है। यह उम्मीद की जाती है कि [cyber](#cyber-protocol) प्रोटोकॉल के विकास के साथ प्रत्येक दौर के वेग में कमी आएगी। यह नायकों के बीच प्रतिस्पर्धा के कारण है। हम इस कार्य क्रम को परिमाण के क्रम को तेज बनाना जानते हैं:

- सर्वसम्मति मापदंडों के अनुकूलन
- रैंक संगणना का बेहतर समानांतरकरण
- एक [बेहतर समय](https://ipfs.io/ipfs/QmbsKzizZVVzPbZvg1qSsNMkwmA3MFufgXb3MFqbSnmPs) सर्वसम्मति से आगे

## मापनीयता

हमें एक आर्किटेक्चर की आवश्यकता है जो हमें इस विचार को महत्व देने की अनुमति देगा कि [Google](https://google.com) को क्या पसंद है। आइए मान लेते हैं, कि नोड कार्यान्वयन, जो कि [Cosmos-SDK](https://github.com/cosmos/cosmos-sdk) पर आधारित है, प्रति सेकंड 10k लेनदेन की प्रक्रिया कर सकता है। इसका मतलब यह होगा, कि हर दिन, कम से कम 8.64 मिलियन उस्ताद प्रत्येक में 100 [सायबरलिंक्स](#cyberlinks) जमा कर सकेंगे, और एक साथ खोज परिणामों को प्रभावित करेंगे। यह खयाल में सभी मान्यताओं को सत्यापित करने के लिए पर्याप्त है, लेकिन, यह कहने के लिए पर्याप्त नहीं है कि यह इंटरनेट के वर्तमान पैमाने पर काम करेगा। हमारी टीम द्वारा किए गए कला अनुसंधान की वर्तमान स्थिति को देखते हुए, हम सुरक्षित रूप से यह बता सकते हैं कि अस्तित्व में कोई आम सहमति तकनीक नहीं है, जो किसी विशेष ब्लॉकचेन को उस आकार में स्केल करने की अनुमति देगा जिसकी हमें आवश्यकता है। इसलिए, हम डोमेन-विशिष्ट [ज्ञान रेखांकन](#knowledge-graph) की अवधारणा को पेश करते हैं।

<p align="center">
  <img src="images/network.png" />
</p>

या तो [go-cyber](https://github.com/cybercongress/go-cyber) को फोर्क करके खुद का डोमेन-विशिष्ट खोज इंजन लॉन्च किया जा सकता है, जो कि \textit{सामान्य सार्वजनिक ज्ञान} पर केंद्रित है। या, बस एक मौजूदा श्रृंखला में मॉड्यूल के रूप में [go-cyber](https://github.com/cybercongress/go-cyber) प्लग करें, जैसे: Cosmos Hub अंतर-ब्लॉकचैन संचार प्रोटोकॉल [प्रासंगिकता मशीनों](#relevance-machine) के बीच सिंक्रनाइज़ेशन अवस्था के समवर्ती तंत्र का परिचय देता है। इसलिए, प्रस्तावित खोज आर्किटेक्चर में, डोमेन-विशिष्ट [प्रासंगिकता मशीन](#relevance-machine) सामान्य ज्ञान से सीखने में सक्षम होगी। जैसे सामान्य ज्ञान डोमेन-विशिष्ट [प्रासंगिकता मशीनों](#relevance-machine) से सीख सकते हैं।

## ब्राउज़र

हम यह कल्पना करने के इच्छुक थे कि प्रस्तावित नेटवर्क web3 ब्राउज़र के साथ कैसे काम करेगा। अपनी निराशा के लिए हम [सक्षम नहीं थे](https://github.com/cybercongress/cyb/blob/master/docs/comparison.md) web3 ब्राउज़र खोजने के लिए जो कार्रवाई में प्रस्तावित दृष्टिकोण की स्थिरता को प्रदर्शित कर सकता है। यही कारण है कि हमने स्क्रैच से एक web3 ब्राउज़र विकसित करने का निर्णय लिया है। [cyb](https://cyb.ai) आपका मित्रवत रोबोट है जिसमें [.cyber](#cyber-protocol) प्रोटोकॉल के साथ बातचीत के लिए एक नमूना [.cyber](https://cyber.page) अनुप्रयोग है।

<p align="center">
  <img src="images/cyb.jpg" />
</p>

प्रसव के एक अच्छे उदाहरण के रूप में, हमने [cyber.page](https://cyber.page/) बनाया है। यह एक web2 गेटवे के माध्यम से प्रोटोकॉल के साथ बातचीत करने के लिए नायकों, उस्तादों और इंजीलवादियों को अनुमति देता है। सीधे IPFS में साइबरलिंक्स बनाएं, पिन कंटेंट बनाएं, ग्रेट वेब सर्च करें, cyber के गवर्नेंस आदि में भाग लें। यह गहराई से खोजकर्ता के रूप में भी काम कर सकता है,  एक वॉलेट और पॉकेट हार्डवेयर वॉलेट, जैसे की लेडजर उपकरण।

वर्तमान खोज स्निपेट बेकार हैं। लेकिन, हम मानते हैं कि विभिन्न प्रकार की सामग्री के लिए [IPLD](https://github.com/ipld/specs) का उपयोग करके उन्हें आसानी से बढ़ाया जा सकता है। आखिरकार, वे [Google](https://google.com) की तुलना में अधिक आकर्षक बन सकते हैं।

<p align="center">
  <img src="images/architecture.png" />
</p>

प्रस्तावित वास्तुकला के कार्यान्वयन के दौरान, हमें कम से कम 3 प्रमुख लाभों का एहसास हुआ है कि [Google](https://google.com) शायद अपने पारंपरिक दृष्टिकोण के साथ वितरित करने में सक्षम नहीं होगा:

- खोज परिणाम आसानी से किसी भी P2P नेटवर्क से दिया जा सकता है: जैसे .cyber वीडियो चला सकते हैं
- भुगतान बटन खोज स्निपेट में सही एम्बेड किए जा सकते हैं। इसका मतलब है कि एजेंट खोज परिणामों के साथ बातचीत कर सकते हैं, जैसे .cyber पर एजेंट एक आइटम खरीद सकते हैं। इसका मतलब यह है कि ई-कॉमर्स एक उल्लेखनीय रूपांतरण रोपण के लिए काफी गुण गा सकता है
- खोज स्निपेट का स्थैतिक होना जरूरी नहीं है, लेकिन इंटरएक्टिव हो सकता है। जैसे .cyber आपके वर्तमान वॉलेट शेष को दे सकता है

## तैनाती

तकनीकी सीमाओं के कारण, हमें 2 टोकन का उपयोग कर पारिस्थितिकी तंत्र को बूटस्ट्रैप करना है: [THC](#thc) और [CYB](#cyber)

- [CYB](#cyb) [cyber](#cyber-protocol) प्रोटोकॉल का मूल टोकन है जो कि टेंडर्मिंट सर्वसम्मति एल्गोरिथ्म द्वारा संचालित है। इसके 3 प्राथमिक उपयोग हैं: (1) सर्वसम्मति के लिए स्टैकिंग, (2) बैंडविड्थ को जमा करने के लिए सीमित करने के लिए [सायबरलिंक](#cyberlinks), और (3) मास्टर्स की इच्छा की अभिव्यक्ति cyber\~Rank की गणना के लिए।

- [THC](#thc) (उच्चारण तकनीक के रूप में) एक रचनात्मक cyber प्रोटो पदार्थ है। [THC](#thc) एक एथेरियम ERC-20 संगत टोकन है जिसका cyber मूल्य पर नियंत्रण के रूप में उपयोगिता मूल्य है, जो की cyber\~Foundation द्वारा (DAO का संचालन करने वाला समुदाय) और वितरण खेल से ETH द्वारा संचालित है। [THC](#thc) एक cyber संगठन के रूप में cyber\~Foundation के निर्माण के दौरान उत्सर्जित होता है। [THC](#thc) की रचनात्मक शक्तियां के अंत से पहले निहित होने पर प्रत्येक 1 [THC](#thc) टोकन प्रति 1 [CYB](#cyb) प्राप्त करने की क्षमता से आती हैं।

दोनों टोकन कार्यात्मक रहते हैं और प्रकृति द्वारा उनकी बहुत अलग उपयोगिता के कारण एक दूसरे से स्वतंत्र रूप से मूल्य ट्रैक कर सकते हैं।

कुल मिलाकर, तैनाती की प्रक्रिया में निम्नलिखित संरचना है:

1. cyber\~Congress लिंक के खेल को दर्शाती है
2. समुदाय लिंक के खेल में भाग लेता है
3. लिंक के खेल से परिणामों के साथ समुदाय एक उत्पत्ति ब्लॉक का सत्यापन और प्रस्ताव करता है
4. cyber\~Congress cyber\~Foundation और cyber\~Auction के लिए अनुबंध दर्शाती है
5. उत्पत्ति के बाद समुदाय cyber\~Auction में भाग लेता है। [CYC](#cyb) टोकन पाने के लिए दाता की हिस्सेदारी [THC](#thc) टोकन में होती है।
6. cyber\~Congress cyber\~Auction के दौरान लगातार [CYB](#cyb) टोकन वितरित करती है
7. cyber\~Congress शेष बचे हुए [CYB](#cyb) और [THC](#thc) टोकन को नष्ट कर देते हैं और प्रारंभिक वितरण प्रक्रिया के अंत में रिपोर्ट मिलता है।

cyber~Congress एक [आरागॉन DAO](https://mainnet.aragon.org/#/cybercongress/0x4feb2bcc5907e7779130c093eef8ff44502c1330) के रूप में एथेरियम में रहती है। यह cyber नेटवर्क में एक [3 में से 2 मल्टीसिग भी संचालित करता है](https://cyber.page/network/cyber/contract/cyber1latzme6xf6s8tsrymuu6laf2ks2umqvdq39v8)। cyber\~Congress ने [cyber](#cyber-protocol) प्रोटोकॉल विकसित किया। cyber के संदर्भ में, कांग्रेस की 2 भूमिकाएँ हैं:

1. प्रारंभिक वितरण कार्यक्रम को लागू करने और निष्पादित करने के लिए, जिसे स्वचालित करना असंभव है। क्योंकि ETH और ATOM के बीच संदेश स्वैपिंग के लिए कोई भरोसेमंद बुनियादी ढांचा नहीं है, cyber\~Congress प्रारंभिक वितरण प्रक्रिया में विफलता का एक भी बिंदु पेश करती है। हमने [CYB](#cyb) टोकन [THC](#thc) स्टेकर्स को मैन्युअल रूप से भेजने का फैसला किया है क्योंकि हमें लगता है कि अब हमारे द्वारा बनाए गए नेटवर्क को लॉन्च करने का सही समय है। हम यह भी मानते हैं कि प्रारंभिक वितरण प्रक्रिया के लिए एक निरंतर नीलामी महत्वपूर्ण है। यदि cyber\~Congress किसी भी संभावित कारणों से वितरण के संदर्भ में अपने दायित्वों को देने में विफल रहती है, तो हम आशा करते हैं कि समुदाय नेटवर्क का त्याग करने और [CYB](#cyb) टोकन वितरित करने में सक्षम होगा जैसा कि वादा किया गया था। उम्मीद है, हर ऑपरेशन को काफी और पारदर्शी तरीके से डिज़ाइन किया गया है। सभी ऑपरेशनों को [cyber नेटवर्क में एक विशेष प्रयोजन के 3 में से 2 मल्टीसिग खाते](https://cyber.page/network/cyber/contract/cyber147drnke967697272rr3ankrkj7pzgwjw47cp2u7j) का उपयोग करके निष्पादित किया जाएगा।

2. [cyber](#cyber-protocol) प्रोटोकॉल के विकास का समर्थन करें जब तक कि समुदाय cyber\~Foundation के रूप में विकास को नहीं ला देता है। गेम ऑफ लिंक्स के दौरान ATOMs में दान [cyber\~Congress Cosmos 3 में से 2 मल्टीसिग](https://www.mintscan.io/account/cosmos1latzme6xfx8srytsuu6laf2ks2humqv2tkd9a) पर वितरित किया जाएगा। सभी ATOM दान जो cyber\~Congress मल्टीसिग में रूट किए जाते हैं, वे इसकी संपत्ति बन जाएंगे। ATOM दान की भूमिका निम्नलिखित है: ATOM के लिए धन्यवाद हम Cosmos और cyber इकोसिस्टम दोनों के विकास में cyber\~Congress के लिए एक प्रतिबद्धता को सुरक्षित करना चाहते हैं। ATOM दान cyber\~Congress को स्टैकिंग पुरस्कारों का उपयोग करने और एक स्थायी प्रवाह तक पहुंचने की अनुमति देगा, [cyber](#cyber-protocol) प्रोटोकॉल के निरंतर वित्त पोषण के लिए और न ही [CYB](#cyb) और ATOM टोकन डंप करने की आवश्यकता के बिना। 

## CYB

Proof-of-stake सिस्टम प्रारंभिक वितरण के साथ मदद नहीं करते हैं। हम मानते हैं कि यदि प्रारंभिक वितरण उद्देश्यपूर्ण, ऊर्जा-कुशलता से, निश्चित रूप से और पारदर्शी रूप से डिजाइन किया गया है, इसलिए सुलभ, प्रारंभिक [ज्ञान ग्राफ](#knowledge-proof) गुणवत्ता और आकार में प्राप्त करेगा।

साइबर प्रोटोकॉल के उत्पत्ति खंड में 1 000 000 000 000 000 CYB (एक petacyb या 1 PCYB) टोकन निम्नानुसार हैं:

- 750 000 000 000 000 CYB टोकन उन लोगों के लिए हैं, जो cyber\~Auction के अंत तक [THC](#thc) टोकन की हिस्सेदारी रखते हैं (cyber\~Congress के भागीदार, ETH में गेम ऑफ थ्रोंस और cyber\~Auction)
- गेम ऑफ लिंक्स के प्रतिभागियों के लिए 150 000 000 000 000 CYB टोकन
- Ethereum, Cosmos और Urbit समुदायों के लिए 100 000 000 000 CYB टोकन एक उपहार के रूप में

<p align="center">
  <img src="images/CYB.svg" />
</p>

उत्पत्ति के बाद, CYB टोकन केवल स्टेकिंग और स्लैशिंग मापदंडों के आधार पर नायकों द्वारा बनाए जा सकते हैं। मूल सहमति यह है कि नए बनाए गए CYB टोकन हितधारकों के अधिकार में हैं।

वर्तमान में CYB टोकन की अधिकतम राशि जैसी कोई चीज नहीं है। यह नेटवर्क के नायकों को दी जाने वाली लगातार मुद्रास्फीति के कारण है। CYB टोकन को uint64 का उपयोग करके कार्यान्वित किया जाता है, इसलिए अतिरिक्त CYB टोकन का निर्माण राज्य परिवर्तनों और रैंक की गणना करने के लिए इसे और अधिक महंगा बनाता है। हम CYB टोकन के पूर्ण प्रारंभिक वितरण और स्मार्ट अनुबंधों की कार्यक्षमता के सक्रियण के बाद शासन प्रणाली द्वारा एक आजीवन मौद्रिक रणनीति स्थापित करने की उम्मीद करते हैं। मुद्रास्फीति के शुरुआती मापदंडों को गेम ऑफ लिंक्स के दौरान शासन के माध्यम से परिभाषित किया जाएगा।

## THC

[Google-जैसी](https://google.com) संरचना का विकल्प बनाने के लक्ष्य के लिए विभिन्न समूहों से असाधारण प्रयास की आवश्यकता होती है। इसलिए, हमने एक कोष के रूप में cyber\~Foundation स्थापित करने का फैसला किया है, जिसका प्रबंधन एक विकेंद्रीकृत इंजन जैसे कि Aragon DAO द्वारा किया जाता है। यह ETH के साथ चार्ज किया जाता है और उन एजेंटों द्वारा प्रबंधित किया जाता है जिन्होंने शुरुआती वितरण में भाग लिया है। यह दृष्टिकोण मूल प्लेटफॉर्म टोकन के अत्यधिक बाजार डंपिंग से सुरक्षा की अनुमति देगा - [CYB](#cyb) अपने काम के पहले वर्षों के भीतर, जिससे, स्थिर विकास सुनिश्चित होगा। इसके अतिरिक्त, यह अंतर्निहित प्लेटफ़ॉर्म में विविधता लाने और प्रोटोकॉल को अन्य सर्वसम्मति कंप्यूटिंग आर्किटेक्चर तक विस्तारित करने की अनुमति देता है, ऐसी आवश्यकता उत्पन्न होनी चाहिए।

दान के लिए टोकन चुनते समय, हमने तीन मुख्य मानदंडों का पालन किया: टोकन होना चाहिए (1) सबसे अधिक तरल में से एक, (2) सबसे आशाजनक, इसलिए एक समुदाय ऐसे दिग्गजों की तुलना में भी प्रतिस्पर्धी होने के लिए एक ठोस निवेश बैग को सुरक्षित कर सकता है जैसे [Google](https://google.com), और (3) किसी भी तीसरे पक्ष पर भरोसा किए बिना, एक नीलामी और परिणामस्वरूप संगठन को निष्पादित करने की तकनीकी क्षमता। इन मानदंडों से मेल खाने वाली एकमात्र प्रणाली एथेरियम है, इसलिए, दान का प्राथमिक टोकन ETH होगा।

उत्पत्ति से पहले cyber\~Foundation ने 750 000 000 000 000 THC (सात सौ पचास terathc) का खनन किया है:

- 600 000 000 000 000 THC टोकन cyber\~Auction अनुबंध को आवंटित किए जाते हैं
- 150 000 000 000 000 THC टोकन cyber\~Congress अनुबंध के लिए आवंटित किए गए हैं

<p align="center">
  <img src="images/THC.svg" />
</p>

All decisions by cyber\~Foundation will be executed based on the results of THC votes. The following parameters will be applied:

- Support: 51\%
- Quorum: 51\%
- Vote duration: 500 hours

## Gift

We want to give the ability to evaluate the proposed approach to as many agents as we can. But, without adding such complexity as KYC and/or captcha. That is why we chose to gift 8% of [CYB](#cyb) tokens in Genesis to Ethereum, 1% to Cosmos, and 1% to Urbit communities. The following rules are applied to reproduce the Genesis:

- Every account within the Ethereum foundation network, with at least 1 outgoing transaction which is not a contract, and holds > 0.001 ETH at block 8080808
- Every non-zero account within Cosmos hub-3 at block 2000000
- Every account which holds galaxies (30%), stars (30%), or planets (40%) at block 10677601 according to the number of objects

The key purpose of this gift is for every account in Genesis to be able to make at least 1 [cyberlink](#cyberlinks) in the space of 24 hours as the network is unloaded. This is why we have decided to make the distribution curve a bit more even, and radically change it to a quadratic curve. Hence, we distribute [CYB](#cyb) tokens proportionally to the square root of each account balance during the snapshots. Because a quadratic design is too easy to game with, we have calculated the amount of the distributed [CYB](#cyb) tokens for the proposed blocks before this fact became known to the public. We do not apply the quadratic rule to Urbit aliens.

## Game of Links

A game for Cosmos hodlers in ATOM. Participants donate ATOM in exchange for CYB. The more ATOM is donated, the higher the price of CYB. The game starts from 1 ATOM per 1 GCYB. The game is over when either 146 days have passed since the beginning of the Takeoff donations, or if the price has increased 5x from the starting price. The price of [CYB](#cyb) during the Takeoff is defined by the following function:

f(c) = 40 * c + 1000 

where f(c) is TCYB price in ATOM, the c is amount of TCYB tokens won during Takeoff.

The key idea is: the better the Takeoff donation round performs, the more payouts the participants in the disciplines will receive. 100 [TCYB](#cyb) is allocated to the participants of the Takeoff donations and 50 [TCYB](#cyb) is allocated for participants of the Game of Links disciplines. All [CYB](#cyb) tokens that remain from the Takeoff, are allocated to the community pool at the end of the game. All [CYB](#cyb) tokens that remain from the disciplines are allocated to cyber\~Congress. In addition to CYB tokens, Game of Links allocates test EUL tokens to all Takeoff donors for the final. A [detailed document](https://cybercongress.ai/game-of-links/) has been published with rules and provisions for the game.

## Cyber\~Auction

A game for Ethereum hodlers in ETH. Participants donate ETH in exchange for THC. The more ETH is donated, the higher the price of THC. The game starts from the price which is 5x closing price of the Takeoff in ETH. The game is over when either 888 days have passed since its inception or if the price has increased 5x from the starting price. During this phase [CYB](#cyb) tokens are continuously distributed by cyber\~Congress, based on the vested [THC](#thc) tokens until the end of the auction. Vested [THC](#thc) tokens provide the ability to receive [CYB](#cyb) tokens accordingly, and voting powers within cyber\~Foundation. The price of [THC](#thc) during Cyber\~Auction is defined by the following function:

g(t)= 1/30 * t * p + 5 * p

where g(t) is TTHC price in ETH, t is amount of TTHC tokens won during cyber\~Auction, p is the resulting price of Takeoff for one CYB converted to ETH at closing moment.

The starting price is designed to give the Takeoff participants 5x premium for their risk of investing in hardware and software infrastructure prior to Genesis. cyber\~Auction gives significant incentives for early participators. After the end of the distribution, participants will be able to unlock their [THC](#thc) tokens and use them as they wish, e.i. transfer, exchange, etc. As a result of the auction, the community will have access to all the donated ETH within the Aragon organization. After the end of cyber\~Auction, all the remaining [THC](#thc) on the cyber\~Auction contract must be provably burned. The following rules apply to [CYB](#cyb) tokens under the [multisig for distribution](https://cyber.page/network/cyber/contract/cyber147drnke9676972jr3anklkj7pzgwjw47cp2u7j):

- cyber\~Congress will not delegate its stake, and as a result, it will remain a passive stake until it will become distributed
- after the end of cyber\~Auction, all the remaining [CYB](#cyb) tokens must be provably burned

## Apps

We assume that the proposed algorithm does not guarantee high-quality knowledge by default. Just like a newborn, it needs to acquire knowledge to develop further. The protocol itself provides just one simple tool: the ability to create a [cyberlinks](#cyberlinks) with an agents stake between two content addresses.

Analysis of the semantic core, behavioural factors, anonymous data about the interests of agents and other tools that determine the quality of search, can be achieved via smart contracts and off-chain applications, such as: [web3 browsers](#browzers), decentralized social networks and content platforms. We believe, that it is in the interest of the community and the masters to build the initial [knowledge graph](#knowledge-graph) and to maintain it. Hence, for the graph, to provide the most relevant search results.

Generally, we distinguish three types of applications for [knowledge graphs](#knowledge-graph):

- Consensus apps. Can be run at the discretion of the [consensus computer](#the-notion-of-a-consensus-computer) by adding intelligent abilities
- On-chain apps. Can be run by the [consensus computer](#the-notion-of-a-consensus-computer) in exchange for gas
- Off-chain apps. Can be implemented by using the [knowledge graph](#knowledge-graph) as an input within an execution environment

The following, imaginable, list of apps consolidates the above-mentioned categories:

Web3 browsers. In reality, browser and search are inseparable. It is hard to imagine the emergence of a full-blown web3 browser which is based on web2 search. Currently, there are several efforts for developing browsers around blockchains and distributed tech. Amongst them are Beaker, Mist, Brave, and Metamask. All of them suffer from trying to embed web2 into web3. Our approach is a bit different. We consider web2 as an unsafe subset for web3. So we have developed an experimental web3 browser, Cyb, showcasing the [cyber](#cyber-protocol) approach to answering queries better and delivering content faster.

Social networks. Social networks are not that mysterious. In any social network content is the king. Hence, provable ranking is the basic building block of any social network. All types of social networks can be easily built on top of a [knowledge graph](#knowledge-graph). Cyber can also create social networks based on relevance between users, which no current network is able to achieve.

Programmable semantics. Currently, the most popular keywords in the gigantic semantic core of [Google](https://google.com) are keywords of apps such as: [Youtube](https://youtube.com), [Facebook](https://facebook.com), [GitHub](https://github.com), etc. However, the developers of those successful apps have very limited ability to explain to [Google](https://google.com) how to structure search results in a better manner. The [cyber](#cyber-protocol) approach gives this power back to developers. Developers are now able to target specific semantics cores and index their apps as they wish.

Search actions. The proposed design enables native support for blockchain (and tangle-alike) assets related activity. It is trivial to design applications which are (1) owned by the creators, (2) appear correctly in the search results and (3) allow a transactable action, with (4) provable attribution of a conversion for a search query. e-Commerce has never been this easy for everyone.

Off-line search. IPFS makes it possible to easily retrieve a document from an environment without a global internet connection. [go-cyber](https://github.com/cybercongress/go-cyber) itself can be distributed by using IPFS. This creates the possibility for ubiquitous, off-line search!

Command tools. Command-line tools can rely on relevant and structured answers from a search engine. Practically speaking, the following CLI tool is possible to implement:

````bash
>  go-cyber earn using 100 GB

Enjoy the following predictions:
- apt install go-filecoin:     0.001   BTC p/ month p/ GB
- apt install siad:            0.0007  BTC p/ month p/ GB
- apt install storjd:          0.0005 BTC p/ month p/ GB

According to the most desirable prediction, I decided to try `mine go-filecoin -limit 107374182400`

Git clone ...
Building go-filecoin
Starting go-filecoin
Creating a wallet using @xhipster seed
Your address is ...
Placing bids ...
Waiting for incoming storage requests ...
````

Search tools, from within CLI will inevitably create a highly competitive market of a dedicated semantic core for robots.

Autonomous robots. Blockchain technology enables the creation of devices that can manage digital assets on their own.

`If a robot can store, earn, spend and invest - they can do everything you can do`

What is needed is a simple, yet a powerful state reality tool with the ability to find particular things. [go-cyber](https://github.com/cybercongress/go-cyber) offers a minimalistic, but a continuously self-improving data source, which provides the necessary tools for programming economically rational robots. According to [top-10,000 English words](https://github.com/first20hours/google-10000-english) the most popular word in the English language is the defining article 'the', which means a pointer to a particular item. This fact can be explained as the following: particular items are of most importance to us. Therefore, the nature of us is to find unique things. Hence, the understanding of unique things is essential for robots too.

Language convergence. A programmer should not care about the language that an agent will be using. We don't need to know in which language the agent is performing their search in. The entire UTF-8 spectrum is at work. The semantic core is open, so competition for answering queries can become distributed across different domain-specific areas. Including the semantic cores for various languages. This unified approach creates an opportunity for cyber\~Bahasa. Since the dawn of the Internet, we observe a process of rapid language convergence. We use truly global words across the entire planet, independently of nationality, language, race, name or Internet connection. The dream of a truly global language is hard to deploy because it is hard to agree on what means what. However, we have the tools to make this dream come true. It is not hard to predict that the shorter a word, the more powerful its cyber\~Rank will be. Global, publicly available list of symbols, words, and phrases sorted accordingly by cyber\~Rank with a corresponding link provided by [go-cyber](https://github.com/cybercongress/go-cyber) can become the foundation for the emergence of a genuinely global language everybody can accept. Recent [scientific advances](https://ipfs.io/ipfs/QmQUWBhDMfPKgFt3NfbxM1VU22oU8CRepUzGPBDtopwap1) in machine translation are breathtaking but meaningless to those who wish to apply them without a Google-scale trained model. The proposed cyber\~Rank offers precisely this.

Self prediction. A [consensus computer](#the-notion-of-a-consensus-computer) can continuously build a [knowledge graph](#knowledge-graph) on its own predicting the existence of [cyberlinks](#cyberlinks) and applying these predictions to its state. Hence, a [consensus computer](#the-notion-of-a-consensus-computer) can participate in the economic consensus of the [cyber](#cyber-protocol) protocol.

Universal oracle. A [consensus computer](#the-notion-of-a-consensus-computer) can store the most relevant data in a key-value storage. Where the key is a CID and the values are the bytes of the actual content. This can be achieved by making a decision every round, in regards to which CID value the agentss want to prune and which value they wish to apply. Based on the utility measure of content addresses within the [knowledge graph](#knowledge-graph). To compute utility measure, heroes check the availability and the size of the content for the top-ranked content addresses within the [knowledge graph](#knowledge-graph), then, weight on the size of the CIDs and its rank. The emergent key-value storage will be available to write for [consensus computer](#the-notion-of-a-consensus-computer) only and not for agents. But, values could be used in programs.

Location-aware search. It is possible to construct [cyberlinks](#cyberlinks) with [Proof-of-Location](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG) based on remarkable existing protocols such as [Foam](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG). Consequently, a location-based search also becomes provable, if web3-agents will mine triangulations and attach [proof-of-location](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG) for every linked chain.

Prediction markets on link relevance. We can implement this idea using the ranking of the [knowledge graph](#knowledge-graph) based on a prediction market on link relevance. An app that allows betting on link relevance, can become a unique source of truth for the direction of terms, as well as, motivate agents to submit more links.

Private cyberlinks. Privacy is fundamental. While we are committed to privacy, achieving implementation of private [cyberlinks](#cyberlinks) is unfeasible for our team up to Genesis. Therefore, it is up to the community to work on WASM programs, that can be executed on top of the protocol. The problem is to compute cyber\~Rank, based on the [cyberlinks](#cyberlinks) submitted by a web3-masters without revealing neither: their previous request nor the public keys. Zero-knowledge proofs, in general, are very expensive. We believe that the privacy of search should be a feature by design, but we are unsure that we know how to implement it at this stage. [Coda](https://ipfs.io/ipfs/Qmdje3AmtsfjX9edWAxo3LFhV9CTAXoUvwGR7wHJXnc2Gk) like recursive Snarks and [MimbleWimble](https://ipfs.io/ipfs/Qmd99xmraYip9cVv8gRMy6Y97Bkij8qUYArGDME7CzFasg) constructions, in theory, can solve part of the privacy concern. But, they are new, untested and anyway, will be more expensive with regards to computations than their transparent alternative.

This is surely not the excessive list of all the possible applications, but a very exciting one indeed.

## Conclusion

We defined and implemented a protocol for provable communication, between consensus computers on relevance. The protocol is based on the simple idea of knowledge graphs, which are generated by agents via the use of cyberlinks. Cyberlinks are processed by a consensus computer using the concept of the relevance machine. The cyber consensus computer is based on CIDv0/CIDv1 and uses go-IPFS and Cosmos-SDK as a foundation. IPFS provides significant benefits with regards to resource consumption. CID as primary objects are robust in their simplicity. For every CID, cyber\~Rank is computed by a consensus computer without a single point of failure. Cyber\~Rank is a CYB token weighted PageRank, with economic protection from sybil attacks and selfish voting. Every round the Merkle root of the rank and graph trees are published. Consequently, every computer can prove to any other computer the relevance of value for a given CID. Sybil resistance is based on bandwidth limiting. The embedded ability to execute programs offers inspiring applications. The starting primary goal is the indexing of peer-to-peer content addresses systems, either stateless, such as: IPFS, Swarm, Sia, Git, BitTorrent, or stateful, such as: Bitcoin, Ethereum and other blockchains and tangles. The proposed semantics of cyberlinking offers a robust mechanism for predicting meaningful relations between objects by the consensus computer itself. The source code of the relevance machine is open-source. Every bit of data accumulated by the consensus computer is available for anyone if one has the resources to process it. The performance of the proposed software implementation is sufficient for seamless interaction. The scalability of the proposed implementation is sufficient to index all self-authenticated data that exist today and can serve it to millions of agents of the Great Web. The blockchain is managed by a Superintelligence, which functions under the Tendermint consensus algorithm with a standard governance module. Though the system provides the necessary utility to offer an alternative for a conventional search engine, it is not limited just to this use case. The system is extendable for numerous applications and makes it possible to design economically rational, self-owned robots, that can autonomously understand objects around them.

## References

1. [Scholarly context adrift](https://ipfs.io/ipfs/QmNhaUrhM7KcWzFYdBeyskoNyihrpHvUEBQnaddwPZigcN)
2. [Brand-new stack](https://ipfs.io/ipfs/Qmf2rKkDPSsvdudwSmdDPbZuYae8XRV26c1wAFCCvg8Dhw)
3. [Search engines information retrieval in practice](https://ipfs.io/ipfs/QmeS4LjoL1iMNRGuyYSx78RAtubTT2bioSGnsvoaupcHR6)
4. [Motivating game for adversarial example research](https://ipfs.io/ipfs/QmNrAFz34SLqkzhSg4wAYYJeokfJU5hBEpkT4hPRi226y9)
5. [An idea of a decentralized search](https://ipfs.io/ipfs/QmXNoGTWLQrcFRb66oS4HafpP1vcLKbVkJrQm4DVvihuoq)
6. [IPFS](https://ipfs.io/ipfs/QmV9tSDx9UiPeWExXEeH6aoDvmihvx6jD5eLb4jbTaKGps)
7. [DAT](https://ipfs.io/ipfs/QmXHGmfo4sjdHVW2MAxczAfs44RCpSeva2an4QvkzqYgfR)
8. [go-cyber](https://github.com/cybercongress/go-cyber)
9. [cosmos-sdk](https://github.com/cosmos/cosmos-sdk)
10. [CIDv1](https://github.com/multiformats/cid#cidv1)
11. [cyber.page](http://cyber.page)
12. [DURA](https://github.com/cybercongress/cyb/blob/dev/docs/dura.md)
13. [Colony](https://ipfs.io/ipfs/QmZo7eY5UdJYotf3Z9GNVBGLjkCnE1j2fMdW2PgGCmvGPj)
14. [Truebit](https://ipfs.io/ipfs/QmTrxXp2xhB2zWGxhNoLgsztevqKLwpy5HwKjLjzFa7rnD)
15. [Thermodynamics of predictions](https://ipfs.io/ipfs/QmP81EcuNDZHQutvdcDjbQEqiTYUzU315aYaTyrVj6gtJb)
16. [PageRank](http://ipfs.io/ipfs/QmbuE2Pfcsiji1g9kzmmsCnptqPEn3BuN3BhnZHrPVsiVw)
17. [RFC-6962](https://ipfs.io/ipfs/QmZpJLmc3T2L1FLUxzvU3P8MBCPe15fEmUyVS7Bz8ZKMhG)
18. [IBC protocol](https://ipfs.io/ipfs/QmSGbrGAPZtR6Q1jHHe8mmS3bLBehKmfp9ZYvrg5ycaZuk)
19. [Tendermint](https://ipfs.io/ipfs/QmaMtD7xDgghqgjN62zWZ5TBGFiEjGQtuZBjJ9sMh816KJ)
20. [Comparison of web3 browsers](https://github.com/cybercongress/cyb/blob/master/docs/comparison.md)
21. [Cyb](https://cyb.ai)
22. [SpringRank](https://ipfs.io/ipfs/QmTJPJ55ePgR2MS1HoAtyqS1mteVLXUjAS4H8W97EEopxC)
23. [Run validator in cyber protocol](https://cybercongress.ai/docs/go-cyber/run_validator/)
24. [Top 10000 english words](https://github.com/first20hours/google-10000-english)
25. [Multilingual neural machine translation](https://ipfs.io/ipfs/QmQUWBhDMfPKgFt3NfbxM1VU22oU8CRepUzGPBDtopwap1)
26. [Foam](https://ipfs.io/ipfs/QmZYKGuLHf2h1mZrhiP2FzYsjj3tWt2LYduMCRbpgi5pKG)
27. [Coda](https://ipfs.io/ipfs/Qmdje3AmtsfjX9edWAxo3LFhV9CTAXoUvwGR7wHJXnc2Gk)
28. [Mimblewimble](https://ipfs.io/ipfs/Qmd99xmraYip9cVv8gRMy6Y97Bkij8qUYArGDME7CzFasg)
29. [Tezos](https://ipfs.io/ipfs/QmdSQ1AGTizWjSRaVLJ8Bw9j1xi6CGLptNUcUodBwCkKNS)
30. [Software 2.0](https://medium.com/@karpathy/software-2-0-a64152b37c35)
31. [Proof-of-history](https://ipfs.io/ipfs/QmbsKzizZVVVzPbZvg1qSsNMkwmA3MFufgXb3MFqbSnmPs)
32. [IPLD](https://github.com/ipld)
33. [cyber\~Congress organization](https://mainnet.aragon.org/#/cybercongress/0x4feb2bcc5907e7779130c093eef8fb44502c1330/)
34. [cyber~Congress in Cyber](https://cyber.page/network/cyber/contract/cyber1latzme6xf6s8tsrymuu6laf2ks2humqvdq39v8)
35. [cyber~Congress in Cosmos](https://www.mintscan.io/account/cosmos1latzme6xf6s8tsrymuu6laf2ks2humqv2tkd9a)
36. [multisig for CYB distribution](https://cyber.page/network/cyber/contract/cyber147drnke9676972jr3anklkj7pzgwjw47cp2u7j)
37. [.cyber](https://github.com/cybercongress/dot-cyber)

## Acknowledgements

1. @hleb-albau
2. @arturalbov
3. @jaekwon
4. @ebuchman
5. @npopeka
6. @belya
7. @serejandmyself


