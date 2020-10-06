# Hime Goindex 
[Cloudflare Workers](https://workers.cloudflare.com/) ve [Google Drive](https://www.google.com/drive/) öğelerini kombine ederek sürücünüzü indexlemenizi sağlar.

[go2index/index.js](https://github.com/Hime-Dev/hime-goindex/go2index) CF Workers script.  

hime-goindex acrou temasını temel almıştır. [acrou/goindex](https://github.com/Aicirou/goindex-theme-acrou/)

[README-Acrou](https://github.com/Hime-Dev/hime-goindex/blob/master/README_zh.md)


## Nasıl Entegre Edilir? 

1. [rclone](https://rclone.org/downloads/) uygulamasını yükleyiniz.
2. `rclone.conf` dosyası içerisinden refresh_token alınız.
3. `index.js` dosyasını indirin https://github.com/Hime-Dev/hime-goindex/tree/master/go2index ve aldığınız `refresh_tokeni` yazınız. 
4. `index.js` içerisindeki tüm kodu kopyalayıp [Cloudflare Workers](https://www.cloudflare.com/) içerisine yazınız.

> Bu projeye katkı sağlamak istiyorsanız, lütfen forkladıktan sonra p.r atınız.

## Ayarlar

### Video

| Option       | Type                       | Default                                                      | Description                                                  |
| ------------ | -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `api`        | String                     | `''`                                                         | External video player api. When this value is not null, all of the following options do not work |
| `autoplay`   | Boolean                    | `true`                                                       | When set to true, the video plays automatically, depending on whether the browser supports the |
| `invertTime` | Boolean                    | `false`                                                      | Display the current time as a countdown rather than an incremental counter. |
| `controls`   | Array, Function or Element | `['play-large', 'restart', 'play', 'progress', 'current-time', 'duration', 'mute', 'volume', 'captions', 'settings', 'pip', 'airplay', 'download', 'fullscreen']` | Which buttons are displayed in the control bar. See more [CONTROLS.md](https://github.com/sampotts/plyr/blob/master/CONTROLS.md#using-default-controls) |
| `settings`   | Array                      | `['quality', 'speed', 'loop']`                               | You can specify which settings to show in the menu           |

Daha fazla bilgi için Plyr dökümantasyonuna bakınız [options](https://github.com/sampotts/plyr#options)

### Ses

| Option      | Type    | Default    | Description                                                  |
| ----------- | ------- | ---------- | ------------------------------------------------------------ |
| `container` | String  | `.aplayer` | No support for changes                                       |
| `fixed`     | Boolean | `true`     | No support for changes                                       |
| `autoplay`  | Boolean | `false`    | audio autoplay                                               |
| `loop`      | String  | `'all'`    | player loop play, values: 'all', 'one', 'none'               |
| `order`     | String  | `'list'`   | player play order, values: 'list', 'random'                  |
| `preload`   | String  | `'auto'`   | values: 'none', 'metadata', 'auto'                           |
| `volume`    | Number  | `0.7`      | default volume, notice that player will remember user setting, default volume will not work after user set volume themselves |
| `audios`    | Array   | `[]`       | Playlists can be preset. [FAQ](#FAQ)                         |

Daha fazla bilgi için APlayer dökümantasyonuna bakınız [options](https://aplayer.js.org/#/home?id=options)

## FAQ

> Liste Sıralmasını Nasıl Değiştirebilirim?

636. Kod satırındaki `params.orderBy` öğesini aşağıdaki gibi değiştiriniz.

```javascript
－ params.orderBy = "folder,name,modifiedTime desc";
＋ params.orderBy = "modifiedTime desc";
```

> Ana Sayfama Nasıl Şarkı Eklerim?

CF Worker'ı açınız ve aşağıdaki "audio" satırını bulduktan sonra örnekteki gibi doldururunuz.

```
audio: {
  audios: [
    {
      name: "Mojito",
      artist: "周杰伦",
      url: "https://xx.mp3",
      lrc: "https://xx.lrc",
      cover: "https://xx.jpg"
    }
  ]
}
```



## Change log

### v1.0.18

- Karanlık tema eklendi.
- Özel gif ve png dosyaları atandı.
- Çoklu hesap bağlama entegre "index.js" eklendi.


## Lisans

[MIT](LICENSE)

