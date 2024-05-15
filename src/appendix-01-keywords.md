## Ek A: Anahtar Kelimeler

Aşağıdaki liste, Rust dilinin şu anki veya gelecekteki kullanımı için ayrılmış anahtar kelimeleri içermektedir. Bu nedenle, bunlar tanımlayıcılar (diğer bir deyişle, [Ham Tanımlayıcılar][raw-identifiers]<!--ignore--> bölümünde tartışacağımız ham tanımlayıcılar dışında) olarak kullanılamazlar. Tanımlayıcılar, fonksiyonların, değişkenlerin, parametrelerin, struct alanlarının, modüllerin, crate'lerin, sabitlerin, makroların, statik değerlerin, özniteliklerin, türlerin, trait'lerin veya yaşam sürelerinin isimleridir.

[raw-identifiers]: #ham-tanımlayıcılar

### Şu Anda Kullanılan Anahtar Kelimeler

Aşağıda, şu anda kullanılan anahtar kelimelerin işlevleriyle birlikte bir listesi bulunmaktadır.

* `as` - temel dönüştürme yapar, bir ögeyi içeren belirli bir trait'i ayırt eder veya `use` ifadelerinde ögeleri yeniden adlandırır
* `async` - mevcut iş parçacığını engellemek yerine bir `Future` döner
* `await` - bir `Future` sonucunun hazır olmasına kadar yürütmeyi askıya alır
* `break` - bir döngüden hemen çıkar
* `const` - sabit öğeleri veya sabit ham işaretçileri tanımlar
* `continue` - bir sonraki döngü yinelemesine devam eder
* `crate` - bir modül yolunda, crate kökünü ifade eder
* `dyn` - bir trait nesnesine dinamik dağıtım yapar
* `else` - `if` ve `if let` kontrol akışı yapıları için geri dönüş sağlar
* `enum` - bir numaralandırma tanımlar
* `extern` - harici bir fonksiyon veya değişkeni bağlar
* `false` - Boolean yanlış (false) değeri
* `fn` - bir fonksiyon veya fonksiyon işaretçi türünü tanımlar
* `for` - bir yineleyiciden ögeleri döngüye alır, bir trait'i uygular veya daha yüksek sıralı bir yaşam süresi belirtir
* `if` - bir koşul ifadesinin sonucuna göre dallanır
* `impl` - doğrudan veya trait işlevselliğini uygular
* `in` - `for` döngü söz diziminin bir parçası
* `let` - bir değişkeni bağlar
* `loop` - koşulsuz olarak döngü yapar
* `match` - bir değeri desenlerle eşleştirir
* `mod` - bir modül tanımlar
* `move` - bir kapanışın tüm yakalamalarının sahipliğini almasını sağlar
* `mut` - referanslarda, ham işaretçilerde veya desen bağlamalarında değişebilirliliği belirtir
* `pub` - struct alanlarında, `impl` bloklarında veya modüllerde genel görünürlüğü belirtir
* `ref` - referansla bağlar
* `return` - bir fonksiyondan döner
* `Self` - tanımladığımız veya uyguladığımız tür için bir tür takma adıdır
* `self` - yöntem konusu veya mevcut modül
* `static` - global değişken veya program yürütme süresinin tamamını kapsayan bir yaşam süresi
* `struct` - bir yapı tanımlar
* `super` - mevcut modülün üst modülü
* `trait` - bir trait tanımlar
* `true` - Boolean doğru (true) değeri
* `type` - bir tür takma adı veya ilişkili tür tanımlar
* `union` - bir [union][unionlink]<!--ignore--> tanımlar; yalnızca bir union bildirimi kullanıldığında anahtar kelimedir
* `unsafe` - güvensiz kodu, fonksiyonları, trait'leri veya uygulamaları belirtir
* `use` - sembolleri kapsama alanına getirir
* `where` - bir türü kısıtlayan hükümleri belirtir
* `while` - bir ifadenin sonucuna göre koşullu olarak döngü yapar

> **Not:** `trait` anahtar kelimesi, Rust dilinde bir trait tanımlamak için kullanılır. Traitler, bir türün sahip olması gereken yöntemlerin ve ilişkili ögelerin bir koleksiyonunu tanımlar. Bir trait, diğer dillerdeki arayüzlere (interface) benzer.

[unionlink]: ../reference/items/unions.html

### Gelecekte Kullanılmak Üzere Ayrılmış Anahtar Kelimeler

Aşağıdaki anahtar kelimeler henüz herhangi bir işlevselliğe sahip değildir, ancak Rust tarafından potansiyel gelecekteki kullanım için ayrılmıştır.

* `abstract`
* `become`
* `box`
* `do`
* `final`
* `macro`
* `override`
* `priv`
* `try`
* `typeof`
* `unsized`
* `virtual`
* `yield`


### Ham Tanımlayıcılar

*Ham tanımlayıcılar*, anahtar kelimeleri normalde izin verilmeyen yerlerde kullanmanıza olanak tanıyan sözdizimidir. Bir ham tanımlayıcıyı, bir anahtar kelimenin önüne `r#` ekleyerek kullanırsınız.

Örneğin, `match` bir anahtar kelimedir. `match` ismini kullanan aşağıdaki fonksiyonu derlemeye çalışırsanız:

<span class="filename">Dosya Adı: src/main.rs</span>

```rust,ignore,does_not_compile
fn match(needle: &str, haystack: &str) -> bool {
    haystack.contains(needle)
}
```

şu hatayı alırsınız:

```text
error: expected identifier, found keyword `match`
 --> src/main.rs:4:4
  |
4 | fn match(needle: &str, haystack: &str) -> bool {
  |    ^^^^^ expected identifier, found keyword
```

Bu hata, match anahtar kelimesini fonksiyon tanımlayıcısı olarak kullanamayacağınızı gösterir. match ismini fonksiyon adı olarak kullanmak için, ham tanımlayıcı sözdizimini şu şekilde kullanmanız gerekir:

<span class="filename">Dosya Adı: src/main.rs</span>

```rust
fn r#match(needle: &str, haystack: &str) -> bool {
    haystack.contains(needle)
}

fn main() {
    assert!(r#match("örnek1", "örnek2"));
}
```

Bu kod, herhangi bir hata olmadan derlenecektir. Tanımlamada ve `main` fonksiyonunda fonksiyon adı olarak kullanılan `r#` önekine dikkat edin.

Ham tanımlayıcılar, anahtar kelime olarak ayrılmış olsa bile istediğiniz kelimeyi tanımlayıcı olarak kullanmanıza olanak tanır. Bu, tanımlayıcı adları seçme özgürlüğü sağlar ve bu kelimelerin anahtar kelime olmadığı bir dilde yazılmış programlarla entegrasyon yapmamıza olanak tanır. Ayrıca, ham tanımlayıcılar, crate'inizin kullandığı Rust sürümünden farklı bir sürümle yazılmış kütüphaneleri kullanmanızı sağlar. Örneğin, `try` 2015 sürümünde anahtar kelime değilken, 2018 sürümünde anahtar kelimedir. Eğer 2015 sürümü kullanılarak yazılmış ve `try` fonksiyonuna sahip bir kütüphaneye bağımlıysanız, 2018 sürümü kodunuzdan bu fonksiyonu çağırmak için ham tanımlayıcı sözdizimini, bu durumda `r#try` kullanmanız gerekir. Sürümler hakkında daha fazla bilgi için [Ek E][appendix-e] bölümüne bakın.

[appendix-e]: appendix-05-editions.html

