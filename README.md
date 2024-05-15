# Rust Programlama Dili

![Yapı Durumu](https://github.com/rust-lang/book/workflows/CI/badge.svg)

Bu depo, "Rust Programlama Dili" kitabının kaynağını içerir.

[Kitap, No Starch Press'ten basılı olarak temin edilebilir][nostarch].

[nostarch]: https://nostarch.com/rust-programming-language-2nd-edition

Ayrıca kitabı çevrimiçi olarak ücretsiz okuyabilirsiniz. Lütfen kitap, en son [kararlı] (stable), [beta] veya [gecelik] (nightly) Rust sürümleriyle gönderildiği şekliyle okuyun. Bu sürümlerdeki sorunların bu depoda zaten düzeltilmiş olabileceğini unutmayın, çünkü bu sürümler daha az sıklıkta güncellenmektedir.

[kararlı]: https://doc.rust-lang.org/stable/book/
[beta]: https://doc.rust-lang.org/beta/book/
[gecelik]: https://doc.rust-lang.org/nightly/book/

Kitapta yer alan tüm kod örneklerinin sadece kodunu indirmek için [sürümler] kısmına bakın.

[sürümler]: https://github.com/rust-lang/book/releases


## Gereksinimler

Kitabı oluşturmak için [mdBook] gereklidir, ideal olarak rust-lang/rust'un [bu dosyada][rust-mdbook] kullandığı sürümle aynı olmalıdır. Bunu edinmek için:

[mdBook]: https://github.com/rust-lang/mdBook
[rust-mdbook]: https://github.com/rust-lang/rust/blob/master/src/tools/rustbook/Cargo.toml

```bash
$ cargo install mdbook --locked --version <sürüm_numarası>
```

## Kitabın Oluşturulması

Kitabı oluşturmak için şu komutu yazın:

```bash
$ mdbook build
```

Çıktı `book` alt dizininde olacaktır. Kontrol etmek için, web tarayıcınızda açın.

_Firefox:_
```bash
$ firefox book/index.html                       # Linux
$ open -a "Firefox" book/index.html             # OS X
$ Start-Process "firefox.exe" .\book\index.html # Windows (PowerShell)
$ start firefox.exe .\book\index.html           # Windows (Cmd)
```

_Chrome:_
```bash
$ google-chrome book/index.html                 # Linux
$ open -a "Google Chrome" book/index.html       # OS X
$ Start-Process "chrome.exe" .\book\index.html  # Windows (PowerShell)
$ start chrome.exe .\book\index.html            # Windows (Cmd)
```

Testleri çalıştırmak için:

```bash
$ mdbook test
```

## Katkıda Bulunma

Yardımınıza ihtiyacımız var! Aradığımız katkı türlerini öğrenmek için lütfen [CONTRIBUTING.md][contrib] dosyasına bakın.

[contrib]: https://github.com/rust-lang/book/blob/main/CONTRIBUTING.md

Kitap [basıldığı][nostarch] ve çevrimiçi versiyonunu mümkün olduğunca basılı versiyona yakın tutmak istediğimiz için, sorununuza veya çekme isteğinize cevap vermemiz alıştığınızdan daha uzun sürebilir.

Şimdiye kadar, [Rust Sürümleri](https://doc.rust-lang.org/edition-guide/) ile örtüşen daha büyük revizyonlar yapıyoruz. Bu büyük revizyonlar arasında, yalnızca hataları düzelteceğiz. Sorununuz veya çekme isteğiniz tam olarak bir hatayı düzeltmiyorsa, bir sonraki büyük revizyon üzerinde çalıştığımız zamana kadar bekleyebilir: bu aylar veya yıllar sürebilir. Sabır gösterdiğiniz için teşekkür ederiz.


### Çeviriler

Kitabın çevirisinde yardıma ihtiyacımız var! Hâlihazırda devam eden çeviri çalışmalarına katılmak için [Çeviriler] etiketine bakın. Yeni bir dil üzerinde çalışmaya başlamak için yeni bir sorun açın! Birden fazla dil desteği için [mdbook desteğini] bekliyoruz, başlamaktan çekinmeyin!

[Çeviriler]: https://github.com/rust-lang/book/issues?q=is%3Aopen+is%3Aissue+label%3ATranslations
[mdbook desteği]: https://github.com/rust-lang/mdBook/issues/5


## Yazım Denetimi

Kaynak dosyalarının hatalarını taramak için, `ci` dizininde bulunan `spellcheck.sh` scriptini kullanabilirsiniz. Bu scriptin, `ci/dictionary.txt` dosyasında sağlanan geçerli kelimeler sözlüğüne ihtiyacı vardır. Eğer script yanlış bir olumlu sonuç verirse (örneğin, `BTreeMap` kelimesini kullandığınızda script bunu geçersiz olarak değerlendirirse), bu kelimeyi `ci/dictionary.txt` dosyasına eklemeniz gerekir (tutarlılık için alfabetik sırayı koruyun).
