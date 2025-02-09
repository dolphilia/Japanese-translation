Protocol

# NSTextInputClient

テキストビューがテキスト入力管理システムと適切に相互作用するために実装しなければならないメソッドのセット。

`macOS 10.5+`

## 宣言

```objc
@protocol NSTextInputClient
```

## 概要

別のテキストビュークラスを作成するには、NSTextViewをサブクラス化するか（歴史的な理由によりNSTextではなく）、NSViewをサブクラス化してNSTextInputClientプロトコルを実装します。

> 重要: NSTextInputClient プロトコルに固有のメソッドは、テキスト入力を扱うことを目的としており、一般に他の目的には適さない。

## トピック

### マークされた文字列の取り扱い

|                     メソッド                     |                                                 説明                                                 |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| \- hasMarkedText                                 | 必須。受信機がテキストをマークしているかどうかを示すブール値を返す。                                 |
| \- markedRange                                   | 必須。マークされたテキストの範囲を返します。                                                         |
| \- selectedRange                                 | 必須。選択されたテキストの範囲を返します。                                                           |
| \- setMarkedText:selectedRange:replacementRange: | 必須。受信機テキストストレージ内の指定された範囲を、与えられた文字列で置き換え、選択範囲を設定する。 |
| \- unmarkText                                    | 必須。マークされた文字列のマークを解除します。                                                       |
| \- validAttributesForMarkedText                  | 必須。受信機で認識できる属性名の配列を返す。                                                         |

### テキストの保存

|                      メソッド                       |                                       説明                                       |
| --------------------------------------------------- | -------------------------------------------------------------------------------- |
| \- attributedSubstringForProposedRange:actualRange: | 必須。受信機テキストストレージ内の指定された範囲に含まれる属性付き文字列を返す。 |
| \- insertText:replacementRange:                     | 必須。指定された文字列を受信機に挿入し、指定された内容を置き換える。             |

### 文字の座標を取得する

|                  メソッド                  |                                  説明                                  |
| ------------------------------------------ | ---------------------------------------------------------------------- |
| \- characterIndexForPoint:                 | 必須。指定された点を含む矩形を境界とする文字のインデックスを返します。 |
| \- firstRectForCharacterRange:actualRange: | 必須。指定された範囲内の文字に対する最初の論理的境界矩形を返します。   |

### バインド・キーストローク

|        メソッド         |                             説明                             |
| ----------------------- | ------------------------------------------------------------ |
| \- doCommandBySelector: | 必須。与えられたセレクタで指定されたアクションを起動します。 |

### オプショナルメソッド

|                  メソッド                  |                                                             説明                                                             |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| \- attributedString                        | 受信機のテキストストレージを表す属性付き文字列を返す。                                                                       |
| \- fractionOfDistanceThroughGlyphForPoint: | 指定された点が、文字の左側から右側までの距離の何分の一であるかを返します。                                                   |
| \- baselineDeltaForCharacterAtIndex:       | firstRectForCharacterRange:actualRange:で返された矩形の原点を基準として、与えられた文字のベースライン位置を返します。        |
| \- windowLevel                             | 受信機のウィンドウレベルを返す。                                                                                             |
| \- drawsVerticallyForCharacterAtIndex:     | プロトコル準拠のクライアントが、指定されたインデックスの文字を縦書きで表示するかどうかをテキスト入力管理システムに通知する。 |

## Relationships

### 継承

NSTextCheckingClient

### Conforming Types

NSTextView

## 参照

### 入力管理

|       クラス       |                                                    説明                                                    |
| ------------------ | ---------------------------------------------------------------------------------------------------------- |
| NSTextInputContext | Cocoaのテキスト入力システムを表すオブジェクトです。                                                        |
| NSTextAlternatives | あるテキストに対する代替文字列のリスト。                                                                   |
| NSTextContent      | 入力コンテンツの種類を具体的に記述したプロトコル。                                                         |
| NSTextInput        | テキストビューがテキスト入力管理システムと適切に相互作用するために実装しなければならないメソッドのセット。 |