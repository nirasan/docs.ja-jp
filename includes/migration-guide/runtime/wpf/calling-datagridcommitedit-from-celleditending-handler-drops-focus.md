### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>CellEditEnding ハンドラーから DataGrid.CommitEdit を呼び出すと、フォーカスが削除される

|   |   |
|---|---|
|説明|<xref:System.Windows.Controls.DataGrid?displayProperty=name> の <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> イベント ハンドラーのいずれかから <xref:System.Windows.Controls.DataGrid.CommitEdit> を呼び出すと、<xref:System.Windows.Controls.DataGrid?displayProperty=name> からフォーカスが失われます。|
|提案される解決策|このバグは .NET framework 4.5.2 で修正されたため、.NET Framework をアップグレードすることによって回避できます。 または、<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name> を呼び出した後で <xref:System.Windows.Controls.DataGrid?displayProperty=name> を明示的に再選択することによって回避できます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

