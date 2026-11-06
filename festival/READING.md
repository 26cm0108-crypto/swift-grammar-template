# 読解ノート：自分のアプリのコード3箇所

> **氏名：** （自分の名前）
> **AI利用レベル：** 1（質問のみ。説明は自分の言葉で書く）
> **最終更新：** YYYY-MM-DD

生成AIに書いてもらったコードでも、自分で書いたコードでもかまいません。自分のアプリの中から3箇所を選んで、次の3つの問いに答えてください。分からないところは、生成AIに「この行は何をしていますか」「この行を消すとどうなりますか」と聞いてかまいません。ただし、書くのは自分の言葉です。

> 💡 担任の先生の指示で、項目が増えることがあります。

---

## 箇所1：（例：品名を追加するボタンの処理）

```swift
private func dameKeisan(_ power: Int, _ kougeki: Int, _ bougyo: Int) -> Int {
    let dame = Double(power)
        * Double(kougeki + 100)
        / Double(bougyo + 100)
    return max(1, Int(dame))
}
```

**何をしているか：**
ダメージの計算をしている

**なぜこう書くのか：**
攻撃力や技の威力が高かったら、ダメージを高くして、防御力が高いならダメージを小さくなるようにするため

**もしこう書かなかったら：**
ダメージが出せなくなる
---

## 箇所2：（見出し）

```swift
if jibunBuki && aiteBuki {
    let jibunTateWaza = self.jibunBuki.bukiNamae == "盾"
    let aiteTateWaza = self.aiteBuki.bukiNamae == "盾"

    if jibunTateWaza != aiteTateWaza {
        jibunFirst = jibunTateWaza
    } else if jibun.subayasa != aite.subayasa {
        jibunFirst = jibun.subayasa > aite.subayasa
    } else {
        jibunFirst = jibunSakini
    }
}
```

**何をしているか：**
武器の行動順を決めている

**なぜこう書くのか：**
同時に武器を使うなら素早さで行動順を決めて、盾は最初に行動できるようにするため

**もしこう書かなかったら：**
武器を使った時の行動順がおかしくなる
---

## 箇所3：（見出し）

```swift
if get(g).hp > 0, get(g).dokuTurn > 0 {
    modify(g) {
        $0.hp = max(0, $0.hp - 20)
        $0.dokuTurn -= 1
    }
    emit("\(mei(g))は毒のダメージを受けた！",
         damejiType: "poison")
}
```

**何をしているか：**
毒状態なら毎ターン20ダメージ与えて、毒状態のターンを-1している

**なぜこう書くのか：**
毒状態の時にダメージを与えて、毒の残りのターンがどのくらい続くかに必要だから

**もしこう書かなかったら：**
毒のダメージを受けない
---

## 自分ではまだ説明できない箇所（正直に）
通信対戦する機能で、近くの人と通信してデータを送っているのはなんとなくわかるが、コードが全くわからない
