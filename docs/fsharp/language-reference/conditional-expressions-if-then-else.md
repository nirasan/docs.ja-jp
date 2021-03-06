---
title: '条件式: if... then...else (F#)'
description: コードの別の分岐を実行するのには、f# で条件付きの式を記述する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: a3ca3c20a659ccf5dc432d0a747ff176ec889e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563134"
---
# <a name="conditional-expressions-ifthenelse"></a>条件式: `if...then...else`

`if...then...else`式は、コードの別の分岐を実行し、別の値によって指定されるブール式を評価することもできます。


## <a name="syntax"></a>構文

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>コメント
前の構文で*expression1*ブール式を評価するときに実行`true`、それ以外の*expression2*を実行します。

異なり、他の言語で、`if...then...else`構造は式、ステートメントではなくです。 つまりを実行する分岐の最後の式の値には、値が生成されます。 各分岐で生成される値の型が一致する必要があります。 明示的ながある場合`else`分岐では、そのタイプが`unit`です。 したがって場合の種類、`then`分岐以外の任意の型は、 `unit`、必要があります、`else`分岐と同じ戻り値の型。 チェーンと`if...then...else`式のキーワードを使用することができます、併せて`elif`の代わりに`else if`; それらが等しい。

## <a name="example"></a>例
次の例を使用する方法を示しています、`if...then...else`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

