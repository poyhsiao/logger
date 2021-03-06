# 在 Virtualbox 中安裝原生 MacOSX 之，以 High Sierra 為例

## 前言

對於一個 MacOSX 的高度依賴者來說，縱使使用 [Ubuntu][ubuntu] 除了介面的部分要稍微適應一下，其他 *command line* 相關的部分，幾乎沒什麼差異或是問題。但是，再怎麼說，不是 *osx* 的環境，沒有許多好用的軟體，縱使覺得礙手礙腳的。對我來說，一定要忍不住抱怨一下以下幾點，我覺得現在的 *Linux* 做的非常好，但是還是有很大的問題。

- 輸入法的問題

    輸入法這問題對我來說實在太重要了，可能對大部分華語為母語的我們來說，都是最基本的吧。對我來說，又有更 ~~~龜毛~~~ 挑剔吧，因為我使用的是標準的 ***拼音輸入法*** 聽起來好像完全沒問題，對吧？但是，身為愛好繁體中文的我來說，故事可不是想的這麼簡單，目前看來，也只有 Android 的 **google 輸入法**，以及 Apple 平台 (iPhone / iPad / Mac) 這幾個原生的輸入法，對於我的要求可以合理的滿足 *我可不要什麼奇怪的簡體字硬翻成繁體的奇怪字詞出現啊*， 像是 *台灣* 而不是 ~~~臺灣~~~，*裡面* 而不是 ~~~裏面~~~，*天后* 而不是 ~~~天後~~~，這些很討厭的問題。當然，這問題在 *Windows* 中更討厭，還硬要換成什麼國籍....不然你永遠找不到。

- 軟體類型的問題

    經過我長期使用 *Mac* 的經驗來說，目前大概 Mac 已經算是主流平台了，幾乎所需要的軟體都有 *Mac* 版本的，而且某些甚至做的比 Windows 平台的還好。那麼，說到使用 *Linux* 不用說也知道，幾乎都要很用力去找替代品。當然不是說沒有好的 *Linux* 專用的軟體，而是，用了就沒朋友或是跟公司的系統無法整合 ( _還是商業操作的問題_ )。所以最好還是裝個虛擬機，執行個 *Windows* 之類的
    
- 效能不彰

    其實，*Linux* 比起 *Windows* 來說，毫無疑問在記憶體控制度和可控性高了非常多，但是，主流的 *desktop management* 還是過於花俏，導致效能不彰。就連我換成非常輕量化的 [LUbuntu] 似乎還是不夠完美，當然 *可能是因為其他原因*，例如 `goa-daemon`
    
好了，抱怨這麼多，如果有個機會，讓我可以在 desktop 的環境中，執行 *MacOSX* 那就太好了。當然，根據我的印象，也只有 [Hackintosh] 可以用，所以根本也只能咬緊牙關，用著 [ubuntu] 還努力尋找相對功能的替代方案。

直到某天，看到 [Virtualbox] 竟然可以安裝 *MacOSX* 這部分，簡直就是我的救星啊，當然得好好研究啦。

## 好吧，先說結論

前面講了這麼多，還是先說結論吧！

1. 真的可以安裝，而且執行的非常不錯 (當然還是有點小問題，後面會說)
2. 可以使用官方下載的安裝檔安裝，相對來說，非常讓人安心 (當然要稍微轉換一下格式)
3. 效能好的驚人 (這部分，真的讓人非常興奮)
4. 用 *Linux* 當 Host OS，會讓你很開心，尤其是如果選了一個超輕量化的 desktop manager

看到這裡，你應該會跟我一樣非常興奮吧，就直接拼了吧，對吧...

## 安裝前準備

### 下載並安裝好最新版的 [Virtualbox]

好啦，為什麼是 [Virtualbox]，其實，理論上應該 [VMware] 應該也可以，不過，那要錢啊，我可不想花錢啊，比較在公司的 desktop 安裝，沒必要破解或是購買，對吧？！另外，我真的不確定是否 [VMware] 可以完整支援安裝 *MacOSX* ，所以我也完全不考慮了。

怎麼下載、安裝，這方面我就不說了，應該沒有什麼特別意外，頂多就是有人會問，要不要安裝 *Extension Pack* 吧？這部分，其實無關是否可以安裝成功，而且我現在用的 desktop 是非常古老的硬體環境，根本沒有像是 *USB 3.0* 這種高級貨，所以，裝不裝，就看你自己的需要吧，我是沒試過是不是有差別 ( _不過我有裝_ )。

### 下載並轉換 High Sierra 成為安裝 ISO 檔

其實理論上，就算把原始的 *High Sierra* 轉換成 USB 開機隨身碟，理論上也可以，不過既然是使用 [virtualbox] 安裝，為了避免你可能遇到的麻煩，或是沒辦法抓到開機的 USB drive ，在這裡還是強烈建議，稍微花點時間，把 *High Sierra* 轉換成 ISO 檔案，或許可以減少你很多白走冤枉路的時間。

首先，當然就是去 [Apple 的 App Store 下載 High Sierra][high sierra]，這部分應該沒有什麼難度把，要注意的是，你應該使用 *Mac* 的機器下載。當然，如果你根本沒有 *Mac* 的機器可以下載，其實，你也可以找 ~~[我(誤)][my]~~ 你的好朋友幫忙。如果你連 *Mac* 的機器都沒辦法借到，那我也只能愛莫能助啦，畢竟接下來要轉換出 ISO 檔，還是會需要 *Mac* 的機器。

![screenshot 2018-05-21 下午5.02.38](https://i.imgur.com/H1WGKPi.jpg)

下載完成後，理論上，系統會自動幫你 *喚起* *High Sierra* 的安裝程式，不過，在此你應該很帥氣的用 `⌘ (command) + q` 的把它關閉，畢竟你現在是要做安裝 ISO 檔。

![screenshot 2018-05-21 下午5.13.17](https://i.imgur.com/vOoViUi.jpg)

你應該可以在你的 *應用程式* 中，找到這個下載的 *High Sierra* 安裝程式，如下圖所示

![screenshot 2018-05-21 下午5.14.45](https://i.imgur.com/wuY65os.jpg)

一直到這邊，應該對你來說沒有任何難度吧！！恭喜你，要準備開始了～～

#### 開始轉換

1. 開啟你喜歡的 *terminal* 應用程式，我是用 iTerm2 ，不過你用其他的也沒差
2. 鍵入以下的 *command*

```bash
# hdiutil create -o /tmp/HighSierra.cdr -size 5200m -layout SPUD -fs HFS+J
```

```bash
# hdiutil attach /tmp/HighSierra.cdr.dmg -noverify -mountpoint /Volumes/install_build
```

```bash
# sudo <你的 High Sierra 安裝檔案位置>/Contents/Resources/createinstallmedia --volume /Volumes/install_build
```

這裡的 `<你的 High Sierra 安裝檔案位置>` 項目，建議使用 *拖放* 的方式，把你的 *High Sierra 安裝檔* 拖放到 *terminal* 中，畢竟，用手打的，有 99% 的機會都會打錯。所以，與此同時，為了珍惜你寶貴的生命，用 *拖放* 的方式，會讓你輕鬆很多的！！

![screenshot 2018-05-21 下午6.09.06](https://i.imgur.com/lhU5Bs3.jpg)


```bash
# mv /tmp/HighSierra.cdr.dmg ~/Desktop/InstallSystem.dmg
```

```bash
# hdiutil detach /Volumes/Install\ macOS\ High\ Sierra
```

```bash
# hdiutil convert ~/Desktop/InstallSystem.dmg -format UDTO -o ~/Desktop/HighSierra.iso
```

```bash
# mv ~/Desktop/HighSierra.iso.cdr ~/Desktop/HighSierra.iso
```

完成以上的步驟後，你應該會在你的 *桌面 / Desktop* 上，出現一個叫做 `HighSierra.iso` 的映像檔

![screenshot 2018-05-21 下午6.55.16](https://i.imgur.com/GVlbhj7.jpg)

*double-click* 這個映像檔後，聰明的 *Mac* 應該就會幫你掛載這個影像檔

![screenshot 2018-05-21 下午6.55.47](https://i.imgur.com/3FIncBb.jpg)

點選掛在的裝置後，接下來應該就可以看到一下的畫面了！！

![screenshot 2018-05-21 下午6.52.28](https://i.imgur.com/Wu24Y21.jpg)

---

到此為止，我們已經順利完成了 *High Sierra* ISO 檔案的製作了，這個 ISO 檔，可是完完全全官方版本，可沒有加入任何調味修飾喔！即使你想要安裝或是復原你的 *Mac* 系統，用這個 ISO 檔操作，也完全沒有問題的！！

### 深呼吸

    
[ubuntu]: https://www.ubuntu.com/ (Ubuntu official site)
[lubuntu]: https://lubuntu.net/ (lubuntu - one family member of Ubuntu)
[hackintosh]: https://hackintosh.com/ (porting version of osx)
[virtualbox]: https://www.virtualbox.org/ (Virtualbox official site)
[high sierra]: https://itunes.apple.com/tw/app/macos-high-sierra/id1246284741?mt=12 (High Sierra 官方下載處)
[my]: mailto:white.shopping@gmail.com

