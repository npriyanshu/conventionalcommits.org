---
draft: false
aliases: ["/hi/"]
---

# Conventional Commits 1.0.0

## सारांश

कन्वेंशनल कमिट्स स्पष्टता से भरपूर कमिट मैसेजेस की एक हल्की परंपरा है।
इसने स्पष्ट कमिट हिस्ट्री बनाने के लिए एक सरल सेट के नियम प्रदान किए हैं;
जिससे कि इस पर स्वचालित उपकरण लिखना आसान हो जाता है।
यह प्रक्रिया [SemVer](http://semver.org) के साथ मेल खाती है,
क्योंकि कमिट मैसेजेस में किए गए विशेषताएँ, फिक्सेस, और ब्रेकिंग चेंजेस को वर्णित करती है।

कमिट मैसेज को निम्नलिखित रूप में संरचित किया जाना चाहिए:

---

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```
---

<br />
इस कमिट में इस पुस्तकालय के उपभोक्ताओं को इरादे को संवेदनशीलता से संवादित करने के लिए निम्नलिखित संरचनात्मक तत्व हैं:

1. **fix:** धराती को एक _प्रकार_ `fix` की कमिट आपके कोडबेस में एक बग पैच करती है (यह सेमांटिक वर्शनिंग में [`PATCH`](http://semver.org/#summary) के साथ संबंधित है)।
1. **feat:** _प्रकार_ `feat` की कमिट आपके कोडबेस में एक नई सुविधा पेश करती है (यह सेमांटिक वर्शनिंग में [`MINOR`](http://semver.org/#summary) के साथ संबंधित है)।
1. **BREAKING CHANGE:** एक कमिट जिसमें एक पैरा है `BREAKING CHANGE:`, या प्रकार/दायरा के बाद एक `!` लगा है, वह एक तोड़ एपी बदलाव पैदा करती है (सेमांटिक वर्शनिंग में [`MAJOR`](http://semver.org/#summary) के साथ संबंधित)।
एक तोड़ एपी बदलाव किसी भी _प्रकार_ की कमिट का हिस्सा हो सकता है।
1. `fix:` और `feat:` के बाहर के _प्रकार_ के अनुमति हैं, उदाहरणार्थ [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional) (जो [एंगुलर नियम](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines) पर आधारित है) `build:`, `chore:`,
  `ci:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:`, और अन्य का सुझाव देता है।
1. `BREAKING CHANGE: <description>` के बाहर के _पैरा_ या _पैरा_ के समान _फूटर_ दिया जा सकता है और एक समान अनुसरण कर सकता है
  [गिट ट्रेलर फॉर्मैट](https://git-scm.com/docs/git-interpret-trailers) के समान हैं।

कनवेंशनल कमिट्स निर्देशनांक द्वारा प्रदान की गई अतिरिक्त प्रकारों की आवश्यकता नहीं है, और इसमें सेमांटिक वर्शनिंग में कोई श्रृंगारिक प्रभाव नहीं है (यदि न कोई वे एक तोड़ एपी शामिल करते हैं)।
<br /><br />
कमिट के _प्रकार_ के लिए एक परिधि प्रदान की जा सकती है, एक कमिट के _प्रकार_ के अतिरिक्त सांदर्भिक जानकारी प्रदान करने के लिए और इसमें बृज में है, उदाहरणार्थ `feat(parser): add ability to parse arrays`।

## उदाहरण

### विवरण और तोड़फोड़ फूटर के साथ कमिट मैसेज
```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

### तोड़फोड़ के लिए ध्यान खींचने के लिए `!` के साथ कमिट मैसेज
```
feat!: send an email to the customer when a product is shipped
```

### दायरा और `!` के साथ तोड़फोड़ के लिए ध्यान खींचने के लिए कमिट मैसेज
```
feat(api)!: send an email to the customer when a product is shipped
```

### `!` और BREAKING CHANGE फूटर के साथ कमिट मैसेज
```
chore!: नोड 6 के लिए समर्थन छोड़ें

BREAKING CHANGE: नोड 6 में उपलब्ध नहीं हैं जावास्क्रिप्ट फीचर्स का उपयोग करें।
```

### शरीर के साथ कमिट मैसेज नहीं
```
docs: CHANGELOG की शब्दावली में शुद्धि
```

### दायरा के साथ कमिट मैसेज
```
feat(lang): पोलिश भाषा जोड़ें
```

### बहु-पैरा शरीर और कई फूटर्स के साथ कमिट मैसेज
```
fix: अनुरोधों का दौड़ना रोकें

नए अनुरोध के लिए एक अनुरोध आईडी और संदर्भ प्रस्तुत करें। विघटन
आने वाले अनुरोधों के अलावा आए हुए प्रतिसादों को खारिज करें
```

## निर्देशन

इस दस्तावेज़ में "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY" और "OPTIONAL" शब्दों का उपयोग [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) में बताए गए रूप में करना चाहिए।

1. कमिट्स को एक प्रकार से प्रारंभ किया जाना चाहिए, जिसमें एक संज्ञान, `feat`, `fix`, आदि, और ऐच्छिक दायरा, ऐच्छिक `!`, और आवश्यक टर्मिनल कोलन और अंतरिक्ष के साथ, शामिल हैं।
1. `feat` टाइप का उपयोग तब होना चाहिए जब कोडबेस में एक नई सुविधा जोड़ता है।
1. `fix` टाइप का उपयोग तब होना चाहिए जब कोडबेस के लिए एक बग फिक्स होता है।
1. एक स्कोप एक टाइप के बाद प्रदान किया जा सकता है। स्कोप में कोडबेस के एक खंड का वर्णन करने वाला एक संज्ञा होनी चाहिए, जो एक समरेखन से घेरी जाती है, उदाहरण के लिए, `fix(parser):`
1. एक विवरण टाइप/स्कोप प्रिफिक्स के बाद कोलन और स्थान के बाद तुरंत होना चाहिए। विवरण कोड परिवर्तनों का एक संक्षेप है, उदाहरण के लिए, _fix: स्ट्रिंग में मल्टीपल स्थानों के साथ एरे पार्सिंग समस्या_।
1. एक और लंबा कमिट शरीर छोटे विवरण के बाद प्रदान किया जा सकता है, जो कोड परिवर्तनों के बारे में अतिरिक्त संदर्भ सूचना प्रदान करता है। शरीर विवरण के बाद एक रिक्त पंक्ति से शुरू होना चाहिए।
1. कमिट शरीर फ्री-फॉर्म है और इसमें किसी भी संख्या की न्यूलाइन से अलग पैराग्राफ हो सकता है।
1. एक से अधिक फूटर्स एक रिक्त पंक्ति के बाद प्रदान किए जा सकते हैं। प्रत्येक फूटर एक शब्द टोकन, जिसके बाद या `:<अंतर>` या `<अंतर>#` विभाजक हो, और एक स्ट्रिंग मूल्य होना चाहिए (यह [गिट ट्रेलर कनवेंशन](https://git-scm.com/docs/git-interpret-trailers) के प्रेरित है)।
1. एक फूटर का टोकन शब्दों की जगह `-` का उपयोग करना चाहिए, उदाहरण के लिए, `Acked-by` (यह फूटर सेक्शन को एक मल्टी-पैरा बॉडी से अलग करने में मदद करता है)। एक छूट का अवतार `BREAKING CHANGE` के लिए भी बनाया जा रहा है, जिसका उपयोग एक टोकन के रूप में किया जा सकता है।
1. एक फूटर का मूल्य अंतरिक्ष और न्यूलाइन को शामिल कर सकता है, और जब अगले मान्य फूटर टोकन/विभाजक जोड़ा जाता है, तो पार्सिंग समाप्त होना चाहिए।
1. ब्रेकिंग चेंजेस को कमिट के टाइप/स्कोप प्रिफिक्स या फिर एक फूटर के रूप में इंडिकेट किया जाना चाहिए।
1. यदि एक फूटर के रूप में शामिल किया जाता है, तो एक ब्रेकिंग चेंज को आलूपक्षिक पूर्वधारित किया जाना चाहिए, जिसके पीछे आवश्यक वर्णन है, उदाहरण के लिए,
_BREAKING CHANGE: environment variables now take precedence over config files_।
1. यदि टाइप/स्कोप प्रिफिक्स में शामिल किया गया है, तो ब्रेकिंग चेंजेस को एक `!` सीधे कोलन के पहले इंडिकेट किया जाना चाहिए। यदि `!` का उपयोग किया गया है, तो `BREAKING CHANGE:` फूटर सेक्शन से छोड़ा जा सकता है,
और कमिट विवरण का उपयोग ब्रेकिंग चेंज का वर्णन करने के लिए किया जाना चाहिए।
1. `feat` और `fix` के अलावा भी आपके कमिट मैसेजों में अन्य टाइप्स का उपयोग किया जा सकता है, उदाहरण के लिए, _docs: update ref docs._
1. कनवेंशनल कमिट्स के जो जानकारी के इकाई हैं, उन्हें उपयोगकर्ताओं द्वारा केस संवेदनशील रूप से नहीं लिया जाना चाहिए, ब्रेकिंग चेंज को छोड़कर (जो उपयोग किया जा रहा है)।
1. BREAKING-CHANGE BREAKING CHANGE के साथ समानार्थी होना चाहिए, जब एक फूटर के रूप में एक टोकन के रूप में इस्तेमाल किया जाता है।

## Conventional Commits का उपयोग क्यों करें

* CHANGELOGs को स्वचालित रूप से उत्पन्न करना।
* सेमैंटिक वर्शन बम्प को स्वचालित रूप से निर्धारित करना (लैंड होने वाले कमिट के प्रकारों के आधार पर)।
* परिवर्तनों के प्रकृति को साथी, सार्वजनिक और अन्य हितधारकों को संवादित करना।
* निर्माण और प्रकाशन प्रक्रियाओं को ट्रिगर करना।
* लोगों को आपके परियोजनाओं में योगदान करना और उन्हें एक से अधिक संरचित कमिट इतिहास की अनुमति देना, जिससे उन्हें अन्वेषित करने की अनुमति मिलती है।

## FAQ

### मैं आरंभिक विकास चरण में कमिट मैसेज कैसे निपटाऊं?

हम आपको यह सुझाव देते हैं कि आप उत्पाद को पहले ही जारी कर दिया है की तरह आगे बढ़ें। सामान्यत: *कोई न कोई*, यदि यह आपके साथी सॉफ़्टवेयर विकसकों हो रहा है, तो उनका उपयोग आपके सॉफ़्टवेयर का उपयोग कर रहा है। उन्हें यह जानना होगा कि क्या ठीक है, क्या टूटता है आदि।

### क्या कमिट शीर्षक में टाइप अपरकेस या लोअरकेस होते हैं?

किसी भी केसिंग का उपयोग किया जा सकता है, लेकिन संरचित रहना सबसे अच्छा है।

### यदि कमिट किसी भी कमिट टाइप्स का अनुसरण करता है, तो मैं क्या करूं?

जब संभव हो, वापस जाएं और एक से अधिक कमिट बनाएं। कनवेंशनल कमिट्स के लाभ का हिस्सा यह है कि यह हमें अधिक व्यवस्थित कमिट और पीआर बनाने के लिए प्रेरित करने की क्षमता है।

### क्या यह तेज़ विकास और तेज़ इटरेशन को नहीं बढ़ावा देता?

यह असंगत रूप से तेज़ी से हरकत करने से नहीं बढ़ावा देता है। यह आपको दिशा-हीन तेज़ी से हरकत करने से बचाने में मदद करता है। यह आपको विभिन्न परियोजनाओं में दीर्घकालिक रूप से विभिन्न योगदाताओं के साथ तेज़ी से हरकत करने में सहायक है।

### क्या कनवेंशनल कमिट्स विकसकों को इसके द्वारा बनाए गए कमिट के प्रकार को सीमित करने की कारण विकसकों को बना सकता है?

कनवेंशनल कमिट्स हमें ऐसे कमिट करने के लिए प्रोत्साहित करता है जैसे सुधार। इसके अलावा, कनवेंशनल कमिट्स की लचीलापन आपकी टीम को उनके खुद के टाइप्स बनाने और उन टाइप्स को समय-समय पर बदलने की अनुमति देती है।

### यह SemVer से कैसे संबंधित है?

`fix` प्रकार के कमिट को `PATCH` रिलीज में अनुवादित किया जाना चाहिए। `feat` प्रकार के कमिट को `MINOR` रिलीज में अनुवादित किया जाना चाहिए। कमिट में `BREAKING CHANGE` होने पर, प्रकार के बिना, उन्हें `MAJOR` रिलीज में अनुवादित किया जाना चाहिए।

### मैं Conventional Commits निर्दिष्टीकरण के लिए अपने एक्सटेंशन्स को कैसे संस्करणित करूं, उदा। `@jameswomack/conventional-commit-spec`?

हम आपको अपने इस विनिर्दिष्टीकरण के लिए SemVer का उपयोग करने की सिफारिश करते हैं (और आपको इन विस्तारों को बनाने के लिए प्रोत्साहित करते हैं!)

### अगर मैंने गलती से गलत कमिट प्रकार का उपयोग किया है, तो मैं क्या करूं?

#### जब आपने स्पष्ट रूप से नहीं किया, लेकिन स्पेक का उपयोग किया, उदा। `fix` के बजाय `feat`

मिलाने या रिलीज़ होने से पहले, हम सुझाव देते हैं कि आप `git rebase -i` का उपयोग करें कमिट इतिहास को संपादित करने के लिए। रिलीज़ के बाद, सफ़ाई विभिन्न उपकरणों और प्रक्रियाओं के अनुसार अलग होगी।

#### जब आपने स्पेक के बाहर किए, उदा। `feat` के बजाय `feet`

यदि किसी स्थिति में, यह एक त्रुटि है अगर एक कमिट पैदा होता है जो कनवेंशनल कमिट्स निर्दिष्टीकरण को पूरा नहीं करता है। इसका अर्थ है कि उस कमिट को उपकरणों द्वारा छोड़ दिया जाएगा जो विनिर्दिष्टीकरण पर आधारित हैं।

### क्या सभी मेरे योगदाताओं को Conventional Commits निर्दिष्टीकरण का उपयोग करना चाहिए?

नहीं! यदि आप गिट पर आधारित वर्कफ़्लो का उपयोग करते हैं, तो मुख्य रखरखाव लोग उन्हें मर्ज करते समय कमिट संदेश को साफ़ कर सकते हैं - आम योगदाताओं के लिए कोई बोझ नहीं। इसके लिए एक सामान्य वर्कफ़्लो यह है कि आपकी git सिस्टम स्वचालित रूप से पुल रिक्ति से कमिट्स को मिलाए और मुख्य रखरखाव व्यक्तिगत के लिए सही git कमिट संदेश दर्ज करने के लिए एक फॉर्म प्रस्तुत करे।

### Conventional Commits खुलासा होने वाले कमिट्स को कैसे निपटाता है?

कोड को पलटना कठिन हो सकता है: क्या आप कई कमिट्स को पलट रहे हैं? यदि आप एक विशेषता को पलटते हैं, तो क्या अगली रिलीज़ बजाय एक पैच नहीं होनी चाहिए?

कनवेंशनल कमिट्स ने पलटने के व्यवहार को स्पष्ट रूप से परिभाषित करने के लिए एक निर्देश नहीं दिया है। इसके बजाय हम उपकरण लेखकों को _types_ और _footers_ की लचीलाता का उपयोग करके उनके पलटने के लिए तर्क विकसित करने की स्वतंत्रता छोड़ते हैं।

एक सिफारिश है कि `revert` प्रकार का उपयोग किया जाए, और एक फूटर जो पलटे गए कमिट SHAs का संदर्भ है:

```
revert: let us never again speak of the noodle incident

Refs: 676104e, a215868
```
