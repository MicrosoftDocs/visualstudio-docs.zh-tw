---
title: 自訂模型總管 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 73dc110b6dec5625b5773039b2309ee5a45900bb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943890"
---
# <a name="customizing-the-model-explorer"></a>自訂模型總管
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以針對您的特定領域語言設計工具中，如下所示變更的外觀和行為的 [總管] 中：  
  
-   變更視窗標題。  
  
-   變更索引標籤圖示。  
  
-   變更節點的圖示。  
  
-   隱藏的節點。  
  
## <a name="changing-the-window-title"></a>變更視窗標題  
 若要變更產生的檔案總管的視窗標題，請選取**總管行為**中**DSL 總管**，然後在**屬性**視窗中，將**標題**屬性，以您想要的標題。  
  
## <a name="changing-the-tab-icon"></a>變更索引標籤圖示  
 若要變更索引標籤圖示 [總管] 中，使用 16 x 16 像素圖示.bmp 檔案中。 將圖示檔案放在 \DslPackage\Resources\] 資料夾中，然後變更 [檔案名稱以**ModelExplorerToolWindowBitmaps.bmp**。 例如，您可以變更[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]setup.ico 圖示為.bmp 格式檔案，並重新命名為**DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**。 產生的設計工具會顯示這個圖示程式總管 中的索引標籤上時一起停駐**方案總管 中**。  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>在 [總管] 節點上設定自訂圖示  
 您可以自訂在總管中的節點，使用檔案總管 節點設定。 下列程序示範如何將圖示新增至節點。  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>若要將圖示新增至 [檔案總管] 節點  
  
1.  建立[!INCLUDE[dsl](../includes/dsl-md.md)]使用工作流程 方案範本的方案。  
  
2.  將包含 16 x 16 像素圖示在.bmp 檔案放**Dsl\Resources**方案中的資料夾。  
  
3.  在  **DSL 總管 中**，以滑鼠右鍵按一下**總管行為**，然後按一下 **加入新的總管節點設定**。  
  
     **ExplorerNodeSettings**下方的節點會出現**自訂節點設定**節點。  
  
4.  選取  **ExplorerNodeSettings**，然後在**屬性**視窗中，將**類別**至**動作項目**。  
  
5.  設定**圖示來顯示**圖示檔的路徑。  
  
6.  轉換所有範本，然後建置並執行方案。  
  
7.  在產生的設計工具中，開啟範例圖表。  
  
     [總管] 中應該會顯示三個**動作項目**具有圖示的節點。  
  
> [!NOTE]
>  如果您已將任何項目，會顯示在 [總管] 中產生的節點圖示，檔案總管的所有節點會都顯示圖示。 如果已設定無圖示，節點會顯示預設圖示。  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>變更顯示在 [總管] 節點的名稱  
 您可以變更模型項目的名稱在總管中顯示的方式。 下列程序示範如何顯示名稱**任務**所參考**註解**註解節點中。  
  
#### <a name="to-display-a-property"></a>若要顯示的屬性  
  
1.  開啟您在先前的程序中建立的方案。  
  
2.  請確定**註解**參考只有單一網域類別，藉由設定的屬性名稱的角色多重性**主體**為 0..1。 屬性名稱應該就**主旨**，且關聯性名稱應該會變成**CommentReferencesSubject**。  
  
3.  在  **DSL 總管 中**，以滑鼠右鍵按一下**總管行為**，然後按一下 **加入新的總管節點設定**。  
  
     **ExplorerNodeSettings**下方的節點會出現**自訂節點設定**節點。  
  
4.  選取  **ExplorerNodeSettings**，然後在**屬性**視窗中，將**類別**至**註解**。  
  
5.  以滑鼠右鍵按一下**註解**節點，然後再按一下**加入新的屬性路徑**。  
  
     新的節點會出現名為**屬性顯示**。  
  
6.  選取**屬性顯示**，然後在**屬性**視窗中，按一下 值欄位**屬性路徑**。 選取 **註解**，然後**CommentReferencesSubject**，然後**FlowElement**。 產生的路徑看起來應該像**CommentReferencesSubject.Subject/ ！主旨**。  
  
7.  在 值欄位**屬性**，選取**名稱**。  
  
8.  轉換所有範本，然後建置並執行您的方案。  
  
9. 在產生的設計工具中，開啟範例圖表。  
  
10. 繪製**註解 Connector**註解項目之間， **Task1**在圖表上的項目。  
  
     [總管] 節點應該會顯示為註解**Task1**。  
  
## <a name="hiding-nodes"></a>隱藏節點  
 您可以在總管中隱藏節點，加上其路徑**隱藏的節點**節點**DSL explorer**。 下列程序示範如何隱藏**註解**節點。  
  
#### <a name="to-hide-an-explorer-node"></a>若要隱藏 [總管] 節點  
  
1.  開啟您在先前的程序中建立的方案。  
  
2.  在  **DSL 總管**，以滑鼠右鍵按一下**總管行為**，然後按一下 **新增網域路徑**。  
  
     A**領域路徑**下方的節點會出現**隱藏節點**。  
  
3.  選取**領域路徑**，然後在**屬性**視窗中，按一下 值欄位**路徑定義**。 選取  **FlowGraph**，然後**FlowGraphHasComments**。 產生的路徑看起來應該像**FlowGraphHasComments.Comments**  
  
4.  轉換所有範本，然後建置並執行您的方案。  
  
5.  在產生的設計工具中，開啟範例圖表。  
  
     [總管] 中應該只會顯示**執行者**節點，而應該不會顯示**註解**節點。  
  
## <a name="see-also"></a>另請參閱  
 [Domain-Specific Language Tools Glossary](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
