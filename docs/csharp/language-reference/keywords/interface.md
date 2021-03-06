---
title: インターフェイス (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 0320b1e287f8c7a3eb7751b68b40120f74e8f61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266543"
---
# <a name="interface-c-reference"></a>インターフェイス (C# リファレンス)
インターフェイスには、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[イベント](../../../csharp/programming-guide/events/index.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)のシグネチャのみが含まれています。 インターフェイスを実装するクラスまたは構造体は、インターフェイス定義で指定されているインターフェイスのメンバーを実装する必要があります。 次の例の `ImplementationClass` クラスは、`SampleMethod` を返す、パラメーターのない `void` メソッドを実装する必要があります。  
  
 使用例を含む詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 インターフェイスは、名前空間またはクラスのメンバーであり、次のメンバーのシグネチャを含むことができます。  
  
-   [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [プロパティ](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [インデクサー](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [イベント](../../../csharp/language-reference/keywords/event.md)  
  
 インターフェイスは、1 つ以上の基底インターフェイスから継承できます。  
  
 基本型のリストに基底クラスとインターフェイスが含まれる場合は、基底クラスがリストの最初に表示されます。  
  
 インターフェイスを実装するクラスは、そのインターフェイスのメンバーを明示的に実装できます。 明示的に実装されているメンバーには、クラス インスタンスではアクセスできません。インターフェイスのインスタンスを使用した場合にのみアクセスできます。  
  
 明示的なインターフェイスの実装の詳細とコード例については、「[明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)」を参照してください。  
  
## <a name="example"></a>例  
 ここでは、インターフェイスの実装例を示します。 この例では、インターフェイスにプロパティ宣言が含まれ、クラスに実装が含まれます。 `IPoint` を実装するクラスのインスタンスには、整数プロパティ `x` および `y` が含まれています。  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)  
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)  
 [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)
