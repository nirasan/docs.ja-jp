---
title: ファースト クラスの値としての関数 (F#)
description: 関数は、f# のプログラミング言語のファースト クラスのステータスに昇格する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: cccff5fcf9de150da26422f80cae032ddf21014c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566666"
---
# <a name="functions-as-first-class-values"></a>ファースト クラスの値としての関数

関数型プログラミング言語の最も大きな特徴は、関数がファースト クラスのステータスに昇格することです。 他の組み込み型の値で実行できる処理はすべて、同等の手間で、関数を使用して実行することもできます。

ファースト クラスのステータスの標準的な基準は次のとおりです。

- 識別子に関数をバインドすることができますか。 つまり、でく名前を付けますか。

- 格納できるデータ構造内の関数など、リスト内

- 関数を関数呼び出しの引数として渡すことができますか。

- 関数呼び出しから関数を返すことができますか。

最後の 2 つのメジャーを定義として知られる仕組み*高階演算*または*高階関数*です。 高階関数は、引数として関数を受け取り、関数呼び出しの結果値として関数を返します。 これらの処理によって、関数型プログラミングの中心となる、関数のマッピングや関数の合成などの機能がサポートされます。


## <a name="give-the-value-a-name"></a>値に名前を付ける

関数がファースト クラスの値である場合は、整数や文字列、その他の組み込みの型に名前を付けることができるのと同様に、関数に名前を付けることができる必要があります。 関数型プログラミングの記述では、これを "値に識別子を束縛する" と表現しています。 F# は[`let`バインド](../language-reference/functions/let-bindings.md)値に名前をバインド:`let <identifier> = <value>`です。 次に、2 つのコード例を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

関数には簡単に名前を付けることができます。 次の例は、という名前の関数を定義`squareIt`識別子をバインドして`squareIt`を[ラムダ式](../language-reference/functions/lambda-expressions-the-fun-keyword.md)`fun n -> n * n`です。 関数 `squareIt` は、1 つのパラメーター `n` を受け取り、このパラメーターの 2 乗を返します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F# では、次に示すより簡潔な構文が用意されており、少量の入力で同じ結果を得ることができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

以降の例では、関数の宣言と他の型の値の宣言の類似性を強調するために、ほとんどの場合に最初の `let <function-name> = <lambda-expression>` というスタイルを使用しています。 ただし、名前付き関数はすべて、簡潔な構文で記述することもできます。 一部の例では、両方の方法を使用して記述しています。


## <a name="store-the-value-in-a-data-structure"></a>値をデータ構造に格納する

ファースト クラスの値はデータ構造に格納できます。 次のコード例では、リストとタプルに値を格納する方法を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

タプルに格納された関数名が実際に関数として評価されることを確認するために、次の例では、`fst` 演算子と `snd` 演算子を使用して、`funAndArgTuple` タプルから 1 番目の要素と 2 番目の要素を抽出します。 タプルの 1 番目の要素は `squareIt`、2 番目の要素は `num` です。 識別子 `num` は、前の例で整数 10 にバインドされています。これは、`squareIt` 関数の有効な引数です。 2 番目の式は、タプルの 1 番目の要素をタプルの 2 番目の要素に適用します。つまり、`squareIt num` となります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

識別子 `num` と整数 10 を入れ替えて使用できるのと同様に、識別子 `squareIt` とラムダ式 `fun n -> n * n` も入れ替えて使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a>値を引数として渡す

値が言語内でファースト クラスのステータスを持つ場合、その値は関数に引数として渡すことができます。 たとえば、整数や文字列を引数として渡すのは一般的です。 次のコードは、F# で引数として渡される整数や文字列を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

関数がファースト クラスのステータスを持つ場合は、同様の方法で関数を引数として渡すことができる必要があります。 これは高階関数の 1 番目の特性です。

次の例で、`applyIt` 関数は 2 つのパラメーター `op` と `arg` を持っています。 1 つのパラメーターを持つ関数を `op` に指定し、その関数の適切な引数を `arg` に渡すと、`op` を `arg` に適用した結果が返されます。 次の例では、関数の引数と整数の引数の両方が、同じように名前を使用して渡されています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

関数を引数として他の関数に送信できる機能は、マップ操作やフィルター操作など、関数型プログラミング言語に共通の抽象化が基礎になっています。 たとえば、マップ操作は、複数の関数で共有される計算を引き受ける高階関数であり、リストを走査し、各要素に対してなんらかの処理を実行し、結果のリストを返します。 整数のリストの各要素をインクリメントしたり、各要素を 2 乗したり、文字列のリストの各要素を大文字に変更したりできます。 計算のエラーが発生しやすい部分は、リストを走査し、返す結果のリストを構築する再帰プロセスです。 この部分はマッピング関数に取り込まれます。 特定のアプリケーションで記述する必要があるのは、各リスト要素に個別に適用する関数 (加算、2 乗、大文字と小文字の変更) だけです。 その関数は、前の例で `squareIt` が `applyIt` に渡されたように、マッピング関数への引数として渡されます。

F# など、ほとんどのコレクション型のマップのメソッドを提供する[一覧](../language-reference/lists.md)、[配列](../language-reference/arrays.md)、および[シーケンス](../language-reference/sequences.md)です。 次の例では、リストを使用しています。 構文は `List.map <the function> <the list>` です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

詳細については、次を参照してください。[一覧](../language-reference/lists.md)です。

## <a name="return-the-value-from-a-function-call"></a>関数呼び出しの結果値を返す

最後に、関数が言語内でファースト クラスのステータスを持つ場合は、整数や文字列などの型を返す場合と同様に、その関数を関数呼び出しの結果値として返すことができる必要があります。

次の関数呼び出しでは、整数を返してそれらを表示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

次の関数呼び出しでは、文字列を返します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

次の関数呼び出しはインラインで宣言されており、ブール値を返します。 表示される値は `True` です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

関数呼び出しの結果値として関数を返すことができるのは、高階関数のもう 1 つの特徴です。 次の例では、1 つの引数 `checkFor` を受け取り、結果値として新しい関数を返す `item` という関数を定義します。 返された関数は、引数 `lst` としてリストを受け取り、その `item` 内で `lst` を検索します。 `item` が存在する場合、関数は `true` を返します。 `item` がない場合、関数は `false` を返します。 前のセクションと同様に、次のコードで使用する、指定されたリスト関数[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)一覧を検索します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

次のコードでは、`checkFor` を使用して新しい関数を作成します。作成された関数は、1 つの引数としてリストを受け取り、そのリストから 7 を検索します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

次の例では、F# における関数のファースト クラスのステータスを使用して、2 つの関数の引数の合成を返す `compose` 関数を宣言します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
さらに短いコードについては、次の「カリー化関数」のセクションを参照してください。


次のコードでは、2 つの関数を `compose` の引数として渡します。どちらの関数も、同じ型の 1 つの引数を受け取ります。 戻り値は、この 2 つの関数の引数の合成である新しい関数です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
F# には、関数を合成する演算子として、`<<` と `>>` の 2 つが用意されています。 たとえば、`let squareAndDouble2 = doubleIt << squareIt` は、前の例の `let squareAndDouble = compose doubleIt squareIt` と同じです。

次に、関数呼び出しの結果値として関数を返し、単純な推測ゲームを作成する例を示します。 ゲームを作成するには、他者に推測してもらう値を `makeGame` に渡して `target` を呼び出します。 `makeGame` 関数からの戻り値は、1 つの引数 (推測) を受け取ってその推測が正しいかどうかを報告する関数です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

次のコードでは、`makeGame` に値 `7` を渡して `target` を呼び出します。 識別子 `playGame` には、返されたラムダ式がバインドされます。 したがって、`playGame` は、`guess` の値を 1 つの引数として受け取る関数になります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a>カリー化関数

前のセクションの例の多くを書き込むより簡潔活用して、暗黙的な*カリー化*f# 関数宣言でします。 カリー化とは、複数のパラメーターを持つ関数を、それぞれが単一のパラメーターを持つ一連の埋め込み関数に変換するプロセスです。 F# では、複数のパラメーターを持つ関数は本質的にカリー化されます。 たとえば、前のセクションの `compose` は、次に示すように、3 つのパラメーターを使用する簡潔なスタイルで記述できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

ただし、`compose4curried` に示すように、この結果は 1 つのパラメーターを持つ関数で、その関数もパラメーターが 1 つの関数を返し、さらにその関数も、パラメーターが 1 つの別の関数を返します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

この関数は、いくつかの方法で呼び出すことができます。 次のそれぞれの例は、18 を返して表示します。 どの例でも、`compose4` を `compose4curried` に置き換えることができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

置き換える前と同じように関数が機能することを確認するには、元のテスト ケースをもう一度試します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
パラメーターをタプルとして囲むことで、カリー化を制限できます。 詳細についてを参照してください「パラメーターのパターン」[パラメーターと引数](../language-reference/parameters-and-arguments.md)です。

次の例では、暗黙的なカリー化を使用して、より短いバージョンの `makeGame` を作成します。 この形式では、`makeGame` が `game` 関数を作成して返す方法の詳細はそれほど明確ではありませんが、同じ結果を返す元のテスト ケースを使用することで確認できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

カリー化の詳細についてを参照してください「部分的なアプリケーションの引数」[関数](../language-reference/functions/index.md)です。


## <a name="identifier-and-function-definition-are-interchangeable"></a>識別子と関数定義の交換可能性
前に示した例において、変数名 `num` は整数 10 に評価されます。したがって、`num` が有効な場所では、当然ながら 10 も有効です。 関数識別子とその値にも、同じことが当てはまります。つまり、関数名を使用できる場所では、その名前にバインドされているラムダ式も使用できます。

次の例では、`Boolean` と呼ばれる `isNegative` 関数を定義し、この関数の名前と関数の定義を同じように使用します。 次の 3 つの例は、すべて `False` を返して表示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

もう 1 歩進めて、`applyIt` にバインドされている値を `applyIt` の代わりに使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>F# におけるファースト クラスの値としての関数 #

前のセクションの各例は、F# の関数が、ファースト クラスの値であるための基準を満たしていることを示しています。

- 関数定義に識別子をバインドできます。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- 関数をデータ構造に格納できます。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- 関数を引数として渡すことができます。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- 関数を関数呼び出しの結果値として返すことができます。
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

F# の詳細については、次を参照してください。、 [f# 言語リファレンス](../language-reference/index.md)です。

## <a name="example"></a>例

### <a name="description"></a>説明

次のコードには、このトピックのすべての例が含まれています。

### <a name="code"></a>コード

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a>関連項目

[リスト](../language-reference/lists.md)

[タプル](../language-reference/tuples.md)

[関数](../language-reference/functions/index.md)

[`let` バインド](../language-reference/functions/let-bindings.md)

[ラムダ式:`fun`キーワード](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
