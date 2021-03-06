---
title: -win32icon (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: ba5c7fcc8fe9e3eaab0a955f4cd1a1e07169049e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C# コンパイラ オプション)
**-win32icon** オプションは、エクスプローラーで出力ファイルを適切に表示する .ico ファイルを出力ファイルに挿入します。  
  
## <a name="syntax"></a>構文  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 出力ファイルに追加する .ico ファイル。  
  
## <a name="remarks"></a>コメント  
 .ico ファイルは[リソース コンパイラ](https://msdn.microsoft.com/library/aa381042.aspx)で作成できます。 リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。 .ico ファイルは .rc ファイルから作成されます。  
  
 .NET Framework リソース ファイルの [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (参照) または [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (アタッチ) をご覧ください。 .res ファイルのインポートについては、[-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) をご覧ください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[アプリケーション]** プロパティ ページをクリックします。  
  
3.  **[アプリケーション アイコン]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、.ico ファイル `rf.ico` をアタッチし、`in.exe` を作成します。  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
