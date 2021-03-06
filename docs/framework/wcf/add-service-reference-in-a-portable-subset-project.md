---
title: ポータブル サブセット プロジェクトでサービス参照を追加する
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 5d094bb1d2d1155565e48850a2f41829a93cff84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460490"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a>ポータブル サブセット プロジェクトでサービス参照を追加する
ポータブル サブセット プロジェクトは、.NET アセンブリ プログラマは 1 つのソース ツリーを保持し、複数の .NET 実装 (デスクトップ、Silverlight、Windows Phone、および XBOX) をサポートしながらビルド システムを有効にします。 ポータブル サブセット プロジェクトは、任意の .NET 実装で使用できる .NET framework アセンブリである .NET ポータブル ライブラリのみを参照します。  
  
## <a name="add-service-reference-details"></a>サービス参照の追加の詳細  
 ポータブル サブセット プロジェクトでサービス参照を追加する場合は、次の制限が適用されます。  
  
1.  <xref:System.Xml.Serialization.XmlSerializer> では、文字エンコーディングのみを使用できます。 SOAP エンコーディングを使用すると、インポート中にエラーが発生します。  
  
2.  <xref:System.Runtime.Serialization.DataContractSerializer> シナリオを使用するサービスの場合、再利用された型をポータブル サブセットからのみ受け取ることを確認するために、データ コントラクト サロゲートが提供されます。  
  
3.  ポータブル ライブラリでサポートされていないバインド (<xref:System.ServiceModel.BasicHttpBinding>、トランザクション フロー、信頼できるセッション、または MTOM エンコーディングがない <xref:System.ServiceModel.WSHttpBinding>、および等価のカスタム バインドを除くすべてのバインド) に依存するエンドポイントは無視されます。  
  
4.  メッセージ ヘッダーは、インポート前にすべての操作におけるすべてのメッセージの説明から削除されます。  
  
5.  非ポータブル属性 (<xref:System.ComponentModel.DesignerCategoryAttribute>、<xref:System.SerializableAttribute>、および <xref:System.ServiceModel.TransactionFlowAttribute>) は、生成されたクライアント プロキシ コードから削除されます。  
  
6.  非ポータブル プロパティ (ProtectionLevel、SessionMode、IsInitiating、IsTerminating) は、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.OperationContractAttribute>、および <xref:System.ServiceModel.FaultContractAttribute> から削除されます。  
  
7.  すべてのサービス操作は、クライアント プロキシ上で非同期操作として生成されます。  
  
8.  非ポータブル型を使用する生成済みのクライアント コンストラクターは削除されます。  
  
9. <xref:System.Net.CookieContainer> インスタンスは、生成されたクライアントで公開されます。  
  
10. コード ジェネレーターのアセンブリとバージョンを示すコメント "`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`" がファイルの先頭に挿入されます。  
  
11. <xref:System.Runtime.Serialization.ISerializable> インターフェイスはサポートされません。  
  
12. Net.Tcp および PollingDuplex バインドはサポートされません。  
  
13. <xref:System.Runtime.Serialization.DataContractSerializer> は常にエラーに対して使用されます。  
  
14. ポータブル サブセット プロジェクトでは <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> はサポートされません。  
  
## <a name="see-also"></a>関連項目  
 [WCF クライアントを使用したサービスへのアクセス](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [ポータブル クラス ライブラリ](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))
