---
title: "自訂 [模型總管] |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords: Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7380d4bcade2e93b7e9ab7302201b67df629e041
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="customizing-the-model-explorer"></a>自訂模型總管
您可以變更的外觀和行為的 [總管] 中您的網域特定語言設計工具，如下所示：  
  
-   變更視窗標題。  
  
-   變更索引標籤圖示。  
  
-   變更節點的圖示。  
  
-   隱藏節點。  
  
## <a name="changing-the-window-title"></a>變更視窗標題  
 若要變更 [總管] 中產生的視窗標題，請選取**總管行為**中**DSL 總管**，然後在**屬性**視窗中，將**標題**屬性，以您想要的標題。  
  
## <a name="changing-the-tab-icon"></a>變更索引標籤圖示  
 若要變更索引標籤圖示的 [總管] 中，使用 16 x 16 像素圖示.bmp 檔案中。 圖示檔案放入 \DslPackage\Resources\ 資料夾，然後變更 檔案名稱以**ModelExplorerToolWindowBitmaps.bmp**。 例如，您可以變更[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]setup.ico 圖示成.bmp 格式檔案，並將它來重新命名**DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**。 產生的設計工具會顯示這個圖示的檔案總管 索引標籤上一起停駐時**方案總管 中**。  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>在 [總管] 節點上設定自訂圖示  
 您可以使用 [總管] 節點設定，在檔案總管中自訂節點。 下列程序示範如何將圖示加入至節點。  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>若要將圖示加入至 [總管] 節點  
  
1.  建立[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]方案使用的工作流程方案範本。  
  
2.  將包含在 16 x 16 像素圖示.bmp 檔案放**Dsl\Resources**方案中的資料夾。  
  
3.  在**DSL 總管**，以滑鼠右鍵按一下**總管行為**，然後按一下 **加入新的總管節點設定**。  
  
     **ExplorerNodeSettings**節點會出現在**自訂節點設定**節點。  
  
4.  選取**ExplorerNodeSettings**，然後在**屬性**視窗中，將**類別**至**執行者**。  
  
5.  設定**圖示來顯示**圖示檔案的路徑。  
  
6.  轉換所有範本，然後建置並執行方案。  
  
7.  在產生的設計工具中開啟範例圖表。  
  
     [總管] 中應該會顯示三個**執行者**有程式圖示的節點。  
  
> [!NOTE]
>  如果您已經設定節點的圖示會顯示在 總管 中產生的任何項目，所有的檔案總管 節點會顯示圖示。 如果已設定無圖示，節點會顯示預設圖示。  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>變更顯示在 [總管] 節點的名稱  
 您可以變更模型項目的名稱在檔案總管中顯示的方式。 下列程序示範如何顯示名稱**工作**所參考**註解**註解節點中。  
  
#### <a name="to-display-a-property"></a>若要顯示的內容  
  
1.  開啟您在先前的程序中建立的方案。  
  
2.  請確定**註解**只有單一網域類別參考所設定的屬性名稱 role 的多重性**主旨**至 0..1。 屬性名稱應該就**主旨**，且此關聯性名稱應該會變成**CommentReferencesSubject**。  
  
3.  在**DSL 總管**，以滑鼠右鍵按一下**總管行為**，然後按一下 **加入新的總管節點設定**。  
  
     **ExplorerNodeSettings**節點會出現在**自訂節點設定**節點。  
  
4.  選取**ExplorerNodeSettings**，然後在**屬性**視窗中，將**類別**至**註解**。  
  
5.  以滑鼠右鍵按一下**註解**節點，然後再按一下**加入新的屬性路徑**。  
  
     新的節點會出現名為**屬性顯示**。  
  
6.  選取**屬性顯示**，然後在**屬性**視窗中，按一下 [值] 欄位的**屬性路徑**。 選取**註解**，然後**CommentReferencesSubject**，然後**FlowElement**。 產生的路徑看起來應該像**CommentReferencesSubject.Subject/ ！主旨**。  
  
7.  在 [值] 欄位的**屬性**，選取**名稱**。  
  
8.  轉換所有範本，然後建置並執行您的方案。  
  
9. 在產生的設計工具中開啟範例圖表。  
  
10. 繪製**註解連接器**註解項目之間和**Task1**在圖表上的項目。  
  
     總管節點應該會顯示為註解**Task1**。  
  
## <a name="hiding-nodes"></a>隱藏節點  
 您可以在檔案總管中隱藏節點加到其路徑**隱藏節點**節點**DSL 總管**。 下列程序示範如何隱藏**註解**節點。  
  
#### <a name="to-hide-an-explorer-node"></a>若要隱藏 [總管] 節點  
  
1.  開啟您在先前的程序中建立的方案。  
  
2.  在**DSL 總管**，以滑鼠右鍵按一下**總管行為**，然後按一下 **新增網域路徑**。  
  
     A**網域路徑**節點會出現在**隱藏節點**。  
  
3.  選取**網域路徑**，然後在**屬性**視窗中，按一下 [值] 欄位的**路徑定義**。 選取**FlowGraph**，然後**FlowGraphHasComments**。 產生的路徑看起來應該像**FlowGraphHasComments.Comments**  
  
4.  轉換所有範本，然後建置並執行您的方案。  
  
5.  在產生的設計工具中開啟範例圖表。  
  
     總管 中應該只顯示**執行者** 節點，並不應該顯示**註解**節點。  
  
## <a name="see-also"></a>另請參閱

[特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)