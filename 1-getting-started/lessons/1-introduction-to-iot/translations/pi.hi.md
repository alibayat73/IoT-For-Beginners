# रास्पबेरी पाई

[रास्पबेरी पाई](https://raspberrypi.org) एक सिंगल-बोर्ड कंप्यूटर है। आप कई तरह के उपकरणों और पारिस्थितिक तंत्रों का उपयोग करके सेंसर और एक्ट्यूएटर जोड़ सकते हैं, और इन पाठों के लिए [ग्रोव](https://www.seeedstudio.com/category/Grove-c-1003.html) नामक हार्डवेयर पारिस्थितिकी तंत्र का उपयोग कर सकते हैं। आप अपने पाई को कोड करेंगे और पायथन का उपयोग करके ग्रोव सेंसर तक पहुंचेंगे।

![एक रास्पबेरी पाई 4](../../../../images/raspberry-pi-4.jpg)

***रास्पबेरी पाई 4. माइकल हेन्ज़लर / [विकिमीडिया कॉमन्स](https://commons.wikimedia.org/wiki/Main_Page) / [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)***

## सेट अप

यदि आप अपने आईओटी हार्डवेयर के रूप में रास्पबेरी पाई का उपयोग कर रहे हैं, तो आपके पास दो विकल्प हैं - आप इन सभी पाठों और कोड के माध्यम से सीधे पाई पर काम कर सकते हैं, या आप दूरस्थ रूप से 'हेडलेस' पाई से कनेक्ट करके अपने कंप्यूटर से कोड कर सकते हैं।

शुरू करने से पहले, आपको ग्रोव बेस हैट को अपने पाई से कनेक्ट करना होगा।

### टास्क - सेटअप

अपने पाई पर ग्रोव बेस हैट स्थापित करें और पाई को कॉन्फ़िगर करें

1. ग्रोव बेस हैट को अपने पाई से कनेक्ट करें। हैट का सॉकेट पाई पर सभी जी.पी.आई.ओ पिनों पर फिट बैठता है, पाई पर मजबूती से बैठाने के लिए सभी तरह से पिन को नीचे की ओर खिसकायें। यह पाई के ऊपर बैठता है उसे ढकते हुए।

    ![ग्रोव हैट फिट करना](../../../../images/pi-grove-hat-fitting.gif)

1. तय करें कि आप अपने पाई को कैसे प्रोग्राम करना चाहते हैं, और नीचे दिए गए संबंधित अनुभाग पर जाएं:

    * [सीधे अपने पाई पर काम करें](#सीधे-अपने-पाई-पर-काम-करें)
    * [पाई को कोड करने के लिए रिमोट एक्सेस](#पाई-को-कोड-करने-के-लिए-रिमोट-एक्सेस)

### सीधे अपने पाई पर काम करें

यदि आप सीधे अपने पाई पर काम करना चाहते हैं, तो आप रास्पबेरी पाई ओएस के डेस्कटॉप संस्करण का उपयोग कर सकते हैं और अपने सभी आवश्यक टूल्स इंस्टॉल कर सकते हैं।

#### टास्क - सीधे अपने पाई पर काम करें

विकास के लिए अपना पाई सेट करें।

1. अपना पाई सेट करने के लिए [रास्पबेरी पाई सेटअप गाइड](https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up) में दिए गए निर्देशों का पालन करें, इसे कीबोर्ड/माउस/मॉनिटर से कनेक्ट करें, अपने वाईफाई या ईथरनेट नेटवर्क से कनेक्ट करें और सॉफ्टवेयर को अपडेट करें। जिस ओएस को आप इंस्टॉल करना चाहते हैं वह **Raspberry Pi OS (32 bit)** है, एस.डी. कार्ड इमेज के लिए रास्पबेरी पाई इमेजर इसे अनुशंसित ओएस (Recommended OS) के रूप में चिह्नित करता है।

ग्रोव सेंसर और एक्चुएटर्स का उपयोग करके पाई को प्रोग्राम करने के लिए, आपको डिवाइस कोड, और ग्रोव हार्डवेयर के साथ इंटरैक्ट करने वाले विभिन्न लाइब्रेरीज़ और उपकरणों को लिखने की अनुमति देने के लिए एक एडीटर स्थापित करने की आवश्यकता होगी।

1. एक बार आपका पाई रीबूट हो जाने के बाद, शीर्ष मेनू बार पर **Terminal** आइकन पर क्लिक करके टर्मिनल लॉन्च करें, या  *Menu -> Accessories -> Terminal* चुनें

1. ओएस और स्थापित सॉफ़्टवेयर अद्यतित है यह सुनिश्चित करने के लिए निम्न आदेश चलाएं:

    ```sh
    sudo apt update && sudo apt full-upgrad --yes
    ```

1. ग्रोव हार्डवेयर के लिए सभी आवश्यक लाइब्रेरीज़ को स्थापित करने के लिए निम्न आदेश चलाएँ:

    ```sh
    curl -sL https://github.com/Seeed-Studio/grove.py/raw/master/install.sh | sudo bash -s -
    ```

    पायथन की शक्तिशाली विशेषताओं में से एक [पिप पैकेज](https://pypi.org) स्थापित करने की क्षमता है - ये अन्य लोगों द्वारा लिखे गए और इंटरनेट पर प्रकाशित कोड के पैकेज हैं। आप अपने कंप्यूटर पर एक कमांड के साथ एक पिप पैकेज स्थापित कर सकते हैं, फिर उस पैकेज को अपने कोड में उपयोग कर सकते हैं। यह ग्रोव इंस्टाल स्क्रिप्ट उन पिप पैकेजों को स्थापित करेगा जिनका उपयोग आप पायथन से ग्रोव हार्डवेयर के साथ काम करने के लिए करेंगे।

1. या तो मेनू का उपयोग करके या टर्मिनल में निम्न कमांड चलाकर पाई को रिबूट करें:

    ```sh
    sudo reboot
    ```

1. एक बार पाई रीबूट हो जाने के बाद, टर्मिनल को फिर से लॉन्च करें और [विजुअल स्टूडियो कोड (वीएस कोड)](https://code.visualstudio.com?WT.mc_id=academic-17441-jabenn) स्थापित करने के लिए निम्न आदेश चलाएं - यह वह संपादक है जिसका उपयोग आप अपने डिवाइस कोड को पायथन में लिखने के लिए करेंगे।

    ```sh
    sudo apt install code
    ```

    एक बार यह इंस्टॉल हो जाने के बाद, वीएस कोड शीर्ष मेनू से उपलब्ध होगा।

    >💁 यदि आपके पास कोई पसंदीदा टूल है, तो आप इन पाठों के लिए किसी भी पायथन आईडीई या संपादक का उपयोग करने के लिए स्वतंत्र हैं, लेकिन पाठ वीएस कोड के उपयोग के आधार पर निर्देश देंगे।

1. पाइलेंस स्थापित करें। यह वीएस कोड के लिए एक एक्सटेंशन है जो पायथन भाषा समर्थन प्रदान करता है। वीएस कोड में इस एक्सटेंशन को स्थापित करने के निर्देशों के लिए [पायलेंस एक्सटेंशन डॉक्यूमेंटेशन](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance&WT.mc_id=academic-17441-jabenn) देखें।

### पाई को कोड करने के लिए रिमोट एक्सेस

पीआई पर सीधे कोडिंग करने के बजाय, इसे आप 'हेडलेस' चला सकते है यानी कि बिना कीबोर्ड/माउस/मॉनिटर जोड़े, और विजुअल स्टूडियो कोड का उपयोग करके अपने कंप्यूटर से कॉन्फ़िगर और कोड कर सकते है।

#### पाई ओएस सेट करें

दूरस्थ रूप से कोड करने के लिए, पीआई ओएस को एसडी कार्ड पर इंस्टॉल करना होगा।

##### टास्क - पाई ओएस सेट करें

हेडलेस पाई ओएस सेट करें।

1. [रास्पबेरी पाई ओएस सॉफ्टवेयर पेज](https://www.raspberrypi.org/software/) से **Raspberry Pi Imager** डाउनलोड करें और इसे इंस्टॉल करें

1. यदि आवश्यक हो तो एडेप्टर का उपयोग करके अपने कंप्यूटर में एक एसडी कार्ड डालें

1. रास्पबेरी पाई इमेजर लॉन्च करें

1. रास्पबेरी पाई इमेजर से, **Chosse OS** बटन चुनें, फिर *Raspberry Pi OS (Other)* चुनें, उसके बाद *Raspberry Pi OS Lite (32-bit)*

    ![रास्पबेरी पाई ओएस लाइट के साथ रास्पबेरी पाई इमेजर चयनित](../../../../images/raspberry-pi-imager.png)

    > रास्पबेरी पाई ओएस लाइट रास्पबेरी पाई ओएस का एक संस्करण है जिसमें डेस्कटॉप यूआई या यूआई आधारित उपकरण नहीं हैं। हेडलेस पाई के लिए इनकी आवश्यकता नहीं होती है और यह इंस्टाल को छोटा और बूट अप समय को तेज बनाता है।

1. **CHOOSE OS** बटन चुनें, फिर अपना एसडी कार्ड चुनें

1. `Ctrl+Shift+X` दबाकर **Advanced Options** लॉन्च करें। एसडी कार्ड में इमेज किए जाने से पहले ये विकल्प रास्पबेरी पाई ओएस के कुछ पूर्व-कॉन्फ़िगरेशन की अनुमति देते हैं।

    1. **Enable SSH** चेक बॉक्स चेक करें, और `pi` उपयोगकर्ता के लिए पासवर्ड सेट करें। यह वह पासवर्ड है जिसका उपयोग आप बाद में पाई में लॉग इन करने के लिए करेंगे।

    1. यदि आप वाईफाई पर पाई से कनेक्ट करने की योजना बना रहे हैं, तो **Configure WiFi** चेक बॉक्स को चेक करें, और अपना वाईफाई SSID और पासवर्ड दर्ज करें, साथ ही अपने वाईफाई देश का चयन करें। यदि आप ईथरनेट केबल का उपयोग करेंगे तो आपको ऐसा करने की आवश्यकता नहीं है। सुनिश्चित करें कि जिस नेटवर्क से आप कनेक्ट हैं वह वही है जिससे आपका कंप्यूटर भी कनेक्ट है।

    1. **Set locale settings** चेक बॉक्स चेक करें, और अपना देश और समय क्षेत्र सेट करें

    1. ** SAVE** बटन चुनें

1. एसडी कार्ड में ओएस लिखने के लिए ** WRITE** बटन चुनें। यदि आप macOS का उपयोग कर रहे हैं, तो आपको अपना पासवर्ड दर्ज करने के लिए कहा जाएगा क्योंकि डिस्क इमेज लिखने वाले अंतर्निहित टूल को इस कार्ये के लिए विशेषाधिकार प्राप्त करने की आवश्यकता होती है।

ओएस एसडी कार्ड पर लिखा जाएगा, और एक बार पूरा हो जाने पर ओएस द्वारा इजेक्ट किया जाएगा, और आपको सूचित किया जाएगा। अपने कंप्यूटर से एसडी कार्ड निकालें, इसे पाई में डालें और पाई को पावर दें।

#### पाई से जुड़ें

अगला कदम पाई को दूरस्थ रूप से एक्सेस करना है। आप इसे `ssh` का उपयोग करके कर सकते हैं, जो macOS, Linux और Windows के नवीनतम संस्करणों पर उपलब्ध है।

##### टास्क - पाई से कनेक्ट करें

पाई को दूरस्थ रूप से एक्सेस करें।

1. टर्मिनल या कमांड प्रॉम्प्ट लॉन्च करें, और पाई से कनेक्ट करने के लिए निम्न आदेश दर्ज करें:

    ```sh
    ssh pi@raspberrypi.local
    ```

    यदि आप Windows पर पुराने संस्करण का उपयोग कर रहे हैं जिसमें `ssh` स्थापित नहीं है, तो आप OpenSSH का उपयोग कर सकते हैं। आप [ओपन एसएसएच इंस्टॉलेशन डॉक्यूमेंटेशन](https://docs.microsoft.com//windows-server/administration/openssh/openssh_install_firstuse?WT.mc_id=academic-17441-jabenn) में इंस्टॉलेशन निर्देश पा सकते हैं।

1. यह आपके पाई से जुड़ना चाहिए और पासवर्ड मांगना चाहिए।

    `<hostname>.local` का उपयोग करके अपने नेटवर्क पर कंप्यूटर खोजने में सक्षम होना Linux और Windows के लिए एक नया फ़ीचर है। यदि आप Linux या Windows का उपयोग कर रहे हैं और आपको होस्टनाम नहीं मिलने के बारे में कोई त्रुटि मिलती है, तो आपको ZeroConf नेटवर्किंग को सक्षम करने के लिए अतिरिक्त सॉफ़्टवेयर स्थापित करने की आवश्यकता होगी (जिसे Apple द्वारा Bonjour भी कहा जाता है):

    1. यदि आप Linux का उपयोग कर रहे हैं, तो अवही को निम्न कमांड का उपयोग करके स्थापित करें:

        ```sh
        sudo apt-get install avahi-daemon
        ```

    1. यदि आप Windows का उपयोग कर रहे हैं, तो ZeroConf को सक्षम करने का सबसे आसान तरीका [विंडोज़ के लिए बोनजोर प्रिंट सर्विसेज](http://support.apple.com/kb/DL999) स्थापित करना है। आप उपयोगिता का नया संस्करण प्राप्त करने के लिए [Windows के लिए आईट्यून्स](https://www.apple.com/itunes/download/) भी इंस्टॉल कर सकते हैं (जो स्टैंडअलोन उपलब्ध नहीं है)।

    > 💁 यदि आप `raspberrypi.local` का उपयोग करके कनेक्ट नहीं कर सकते हैं, तो आप अपने पाई के आईपी ​​​​एड्रेस का उपयोग कर सकते हैं। आईपी ​​​​एड्रेस प्राप्त करने के कई तरीकों के निर्देशों के लिए [रास्पबेरी पाई आईपी एड्रेस डॉक्यूमेंटेशन](https://www.raspberrypi.org/documentation/remote-access/ip-address.md) देखें।

1. रास्पबेरी पाई इमेजर एडवांस्ड ऑप्शंस में आपके द्वारा सेट किया गया पासवर्ड दर्ज करें

#### Pi पर सॉफ़्टवेयर कॉन्फ़िगर करें

एक बार जब आप पीआई से जुड़ जाते हैं, तो यह सुनिश्चित करने की ज़रूरत है कि आपका ओएस अप्डेटेड है, और ग्रोव हार्डवेयर के साथ बातचीत करने वाले विभिन्न लाइब्रेरीज़ और उपकरणों को स्थापित/इंस्टॉल  करें।

##### कार्य - Pi पर सॉफ़्टवेयर कॉन्फ़िगर करें

पूर्व-स्थापित पाई सॉफ्टवेयर को कॉन्फ़िगर करें और ग्रोव लाइब्रेरीज़ स्थापित करें।

1. अपने `ssh` सत्र से, अद्यतन करने के लिए निम्नलिखित कमांड चलाएँ और फिर पाई को रिबूट करें:

    ```sh
    sudo apt update && sudo apt full-upgrade --yes && sudo reboot
    ```

    पाई को अपडेट और रीबूट किया जाएगा। Pi के रीबूट होने पर `ssh` सत्र समाप्त हो जाएगा, इसलिए इसे लगभग 30 सेकंड के लिए छोड़ दें और फिर से कनेक्ट करें।

1. फिर से जुड़े `ssh` सत्र से, ग्रोव हार्डवेयर के लिए सभी आवश्यक लाइब्रेरीज़ स्थापित करने के लिए निम्न आदेश चलाएँ:

    ```sh
    curl -sL https://github.com/Seeed-Studio/grove.py/raw/master/install.sh | sudo bash -s -
    ```

    पायथन की शक्तिशाली विशेषताओं में से एक [पिप पैकेज](https://pypi.org) स्थापित करने की क्षमता है - ये अन्य लोगों द्वारा लिखे गए कोड के पैकेज हैं और इंटरनेट पर प्रकाशित होते हैं। आप अपने कंप्यूटर पर एक कमांड के साथ एक पिप पैकेज स्थापित कर सकते हैं, फिर उस पैकेज को अपने कोड में उपयोग कर सकते हैं। यह ग्रोव इंस्टाल स्क्रिप्ट उन पिप पैकेजों को स्थापित करेगा जिनका उपयोग आप पायथन से ग्रोव हार्डवेयर के साथ काम करने के लिए करेंगे।

1. निम्न आदेश चलाकर पाई को रीबूट करें:

    ```sh
    sudo reboot
    ```

    पाइ के रीबूट होने पर `ssh` सत्र समाप्त हो जाएगा। पुन: कनेक्ट करने की कोई आवश्यकता नहीं है।

#### रिमोट एक्सेस के लिए वीएस कोड कॉन्फ़िगर करें

एक बार पाई कॉन्फ़िगर हो जाने के बाद, आप अपने कंप्यूटर से विजुअल स्टूडियो कोड (वीएस कोड) का उपयोग करके इससे जुड़ सकते हैं - यह एक मुफ्त डेवलपर टेक्स्ट एडिटर है जिसका उपयोग आप अपने डिवाइस कोड को पायथन में लिखने के लिए करेंगे।

##### कार्य - रिमोट एक्सेस के लिए वीएस कोड कॉन्फ़िगर करें

आवश्यक सॉफ़्टवेयर स्थापित करें और दूरस्थ रूप से अपने पाई से कनेक्ट करें।

1. [वीएस कोड प्रलेखन](https://code.visualstudio.com?WT.mc_id=academic-17441-jabenn) का पालन करके अपने कंप्यूटर पर वीएस कोड स्थापित करें।

1. आवश्यक घटकों को स्थापित करने के लिए [एसएसएच दस्तावेज़ीकरण का उपयोग कर वीएस कोड रिमोट डेवलपमेंट](https://code.visualstudio.com/docs/remote/ssh?WT.mc_id=academic-17441-jabenn) में दिए गए निर्देशों का पालन करें।

1. समान निर्देशों का पालन करते हुए, VS कोड को पाइ से कनेक्ट करें

1. कनेक्ट होने के बाद, [पाइलेंस एक्सटेंशन](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance&WT.mc_id=academic-17441-jabenn) इंस्टॉल करने के लिए [मैनेजिंग एक्सटेंशन](https://code.visualstudio.com/docs/remote/ssh#_managing-extensions?WT.mc_id=academic-17441-jabenn) निर्देशों का पालन करें।

## हैलो वर्ल्ड

एक नई प्रोग्रामिंग भाषा या तकनीक के साथ शुरू करते समय यह पारंपरिक है कि हम एक छोटे से एप्लिकेशन का निर्माण करें जो हैलो वर्ल्ड प्रिंट करता हो - यह दिखाने के लिए कि सभी टूल्स सही तरीके से कॉन्फ़िगर किए गए हैं

पाई के लिए हैलो वर्ल्ड ऐप यह सुनिश्चित करेगा कि आपके पास पायथन और विजुअल स्टूडियो कोड सही तरीके से स्थापित है।

यह ऐप `नाइटलाइट` नामक फ़ोल्डर में होगा, और नाइटलाइट एप्लिकेशन बनाने के लिए इस असाइनमेंट के बाद के हिस्सों में हैलो वर्ल्ड को अलग-अलग कोड के साथ फिर से उपयोग किया जाएगा।

### कार्य - हैलो वर्ल्ड लिखना

हेलो वर्ल्ड ऐप बनाएं।

1. वीएस कोड लॉन्च करें, या तो सीधे पीआई पर, या अपने कंप्यूटर पर और रिमोट एसएसएच एक्सटेंशन का उपयोग करके पाई से कनेक्ट करें

1. *Terminal -> New Terminal* या `` CTRL+` `` दबाकर VS कोड टर्मिनल लॉन्च करें। यह `pi` उपयोगकर्ताओं की होम निर्देशिका के लिए खुलेगा।

1. अपने कोड के लिए एक निर्देशिका बनाने के लिए निम्नलिखित कमांड चलाएँ, और उस निर्देशिका के अंदर `app.py` नामक एक पायथन फ़ाइल बनाएँ:

    ```sh
    mkdir nightlight
    cd nightlight
    touch app.py
    ```

1. इस फोल्डर को VS कोड में खोलें *File -> Open...*  का चयन करें और *नाइटलाइट*  फोल्डर का चयन करें, फिर **ओके** दबाएं

    ![वी.एस. कोड ओपन डायलॉग जो नाइटलाइट फोल्डर दिखा रहा है](../../../../images/vscode-open-nightlight-remote.png)

1. वीएस कोड एक्सप्लोरर से `app.py` फ़ाइल खोलें और निम्नलिखित कोड जोड़ें:

    ```python
    print('Hello World!')
    ```

    `print` फ़ंक्शन कंसोल पर जो कुछ भी पास किया जाता है उसे प्रिंट करता है।

1. वीएस कोड टर्मिनल से, अपना पायथन ऐप चलाने के लिए निम्नलिखित चलाएँ:

    ```sh
    python3 app.py
    ```

    > 💁 इस कोड को चलाने के लिए आपको स्पष्ट रूप से `python3` को कॉल करने की आवश्यकता है, यदि आपके पास Python 3 (नवीनतम संस्करण) के अलावा Python 2 भी स्थापित है। यदि ऐसा है, तो `python` को कॉल करने से Python 3 के बजाय Python 2 का उपयोग किया जाएगा

    आपको निम्न आउटपुट देखना चाहिए:

    ```output
    pi@raspberrypi:~/nightlight $ python3 app.py
    Hello World!
    ```

> 💁 आप इस कोड को [code/pi](code/pi) फोल्डर में पा सकते हैं।

😀 आपका 'हैलो वर्ल्ड' प्रोग्राम सफल रहा!
