---
title: '方法 : 楕円または円を描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 69620d81eb77eb76f21f099b30017b142d818457
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559367"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>方法 : 楕円または円を描画する
この例を使用して楕円および円を描画する方法を示しています、<xref:System.Windows.Shapes.Ellipse>要素。 楕円を描画するには、作成、<xref:System.Windows.Shapes.Ellipse>要素を指定し、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>です。 使用してその<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティを指定する、<xref:System.Windows.Media.Brush>楕円の内部を塗りつぶすために使用されます。 使用してその<xref:System.Windows.Shapes.Shape.Stroke%2A>プロパティを指定する、<xref:System.Windows.Media.Brush>楕円のアウトラインを描画するために使用されます。 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>プロパティは、楕円アウトラインの太さを指定します。  
  
 円を描画するように、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>の<xref:System.Windows.Shapes.Ellipse>要素を互いに等しくします。  
  
 次の例では、次の 4 つを描画<xref:System.Windows.Shapes.Ellipse>内の要素、<xref:System.Windows.Controls.Canvas>です。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 この例を使用しますが、 <xref:System.Windows.Controls.Canvas> 、省略記号を含むで使用できる楕円要素 (およびその他のすべての図形要素) いずれかの<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。  
  
 この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)
