---
title: WorkflowApplication ReadLine ホスト
ms.date: 03/30/2017
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
ms.openlocfilehash: 8da8a5bb4c80a86fe5ae9e133ea545c00ee17fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518539"
---
# <a name="workflowapplication-readline-host"></a>WorkflowApplication ReadLine ホスト
このサンプルは、汎用 ReadLine ホストです。 用意されている `ReadLine` アクティビティ (または文字列を使用して再開されるブックマークからデータを取得する他の同様のアクティビティ) を使用して、任意のワークフローを読み込んで実行することができます。 `WriteLine` アクティビティ、または <xref:System.Activities.Statements.WriteLine.TextWriter%2A> 拡張に書き込みを行うアクティビティからの出力は、ホスト ウィンドウに送られます。 インスタンスがアイドル状態の場合、そのインスタンスの使用可能なブックマークがコンボ ボックスに表示されます。 ブックマークを選択してテキストを入力し、ブックマークを再開するボタンをクリックすると、ワークフローの実行が続行されます。 選択したワークフローを取り消したり、中止または終了することもできます。 既定では永続化が有効になっており、ホストをシャットダウンして再起動しても、データベースに格納されているインスタンスがインスタンスの一覧に読み込まれます。 <xref:System.Activities.WorkflowApplication> レベルのイベントをホストに出力するには、追跡を使用します。オプションで、アクティビティ レベルの詳細な追跡も行うことができます。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このホストには、ビューとインスタンス マネージャーの 2 つのレイヤーがあります。 ビューは、`HostView` クラスと `WorkflowApplicationInfo` クラスで構成されます。 このホストの一般的なパターンでは、`HostView` クラスを使用して、対象のインスタンスと適切に同期された `WorkflowApplicationInfo` オブジェクトに基づいて、ユーザーに使用可能なオプションを表示します。 インスタンス マネージャー レイヤーは、すべてのホスト通信の中核となる `WorkflowApplicationManager` クラス、インスタンスとそれを開始するのに使用されたプログラム定義との関係を永続化する `WorkflowDefinitionExtension` クラス、およびその他のいくつかのクラスで構成されます。 `HostView` から、`WorkflowApplicationManager` に対する制御操作の呼び出しが行われます。 これらの呼び出しは、通常、ユーザー インターフェイスの応答性を維持するために非同期で実行されます。 非同期呼び出しが完了すると、`WorkflowApplicationManager` から、適切に定義されたインターフェイス (`IHostView`) を介してビュー レイヤーにコールバックされます。 `HostView` クラスは、ほとんどの場合、`WorkflowApplicationManager` クラスからのこれらの呼び出しをユーザー インターフェイス スレッドにディスパッチします。 <xref:System.Activities.Statements.WriteLine.TextWriter%2A> クラスで提供されるスレッド セーフな `HostView` オブジェクトへのテキストの書き込みが実行されます。 イベントを生成する方法はユーザー インターフェイスだけではありません。 たとえば、<xref:System.Activities.WorkflowApplication> オブジェクトも、状態が `WorkflowApplicationManager`、`Idle`、または `Complete` になると `Aborted` に通知します。 `WorkflowApplicationManager` クラスは、ホストにクリーンアップ処理または更新処理をディスパッチしてイベント スレッドを削除します。  
  
 <xref:System.Activities.WorkflowApplication> の起動に使用されたファイルは、`WorkflowDefinitionExtension` クラスを使用して簡単に記録することができます。 このクラスは、永続化に参加してワークフロー定義のパスを永続化するために、<xref:System.Activities.Persistence.PersistenceIOParticipant> インターフェイスを実装します。  
  
 `WorkflowApplicationManager.Load` メソッドは、格納されているパスを使用して、未完了の <xref:System.Activities.WorkflowApplication> オブジェクトの読み込みに必要なワークフロー プログラムをインスタンス化します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  このサンプルを実行するには、SQL Express がインストールされている必要があります。 SQL Express は [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] に付属しています。  
  
2.  Visual Studio 2010 コマンド プロンプトを開きます。  
  
3.  サンプル ディレクトリ (\WF\Basic\Execution\ControllingWorkflowApplications) に移動して、CreateInstanceStore.cmd を実行します。  
  
4.  CreateInstanceStore.cmd スクリプトは、SQL Server 2008 Express の既定のインスタンスにデータベースを作成しようとします。 別のインスタンスにデータベースをインストールする場合は、そのようにスクリプトを変更してください。  
  
5.  WorkflowApplicationReadLineHost プロジェクトをコンパイルし、コマンド ラインから実行します。  
  
6.  実行後、永続化を有効にするか無効にするかを必要に応じて切り替えることができます。 また、詳細なアクティビティ追跡についても、有効にするか無効にするかを切り替えることができます。  
  
7.  横に、省略記号ボタンを押して、**実行**をワークフローの XAML ファイルで定義されている参照ボタンをクリックします。  
  
     SampleWorkflows フォルダーには、サンプルが 2 つあります。 parallel1.xaml サンプルはアイドル状態になります。  
  
8.  例を選択すると、キーを押して、**実行**ボタンをクリックします。  
  
9. 場合、またはワークフローがアイドル状態になったときに、**ブックマーク**コンボ ボックスには、使用可能なブックマークが設定されます。  
  
10. ここで、ブックマークの再開や、ワークフローの取り消し、中止、または終了を実行できます。 また、ホストをシャットダウンして再起動することもできます。 永続化を有効なままにしてあれば、シャットダウン時にインスタンスがアンロードされ、起動時に再度読み込まれます。  
  
     ブックマークを再開するには、目的のブックマークの選択、キーを押して、コンボ ボックスの横にあるテキスト ボックスに値を入力**ブックマークの再開**です。  
  
#### <a name="to-remove-the-instance-store-database"></a>インスタンス ストア データベースを削除するには  
  
1.  Visual Studio 2010 コマンド プロンプトを開きます。  
  
2.  サンプル ディレクトリ (\WF\Basic\Execution\ControllingWorkflowApplications) に移動して、RemoveInstanceStore.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`