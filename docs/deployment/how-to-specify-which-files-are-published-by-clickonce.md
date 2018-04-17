---
title: 如何： 指定哪些檔案由 ClickOnce 發行 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: eee0e88b23a26ae7a89005ff304b565dd3d84c34
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>如何：指定哪些檔案是由 ClickOnce 發行
發行時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]以及應用程式部署應用程式中，所有非程式碼專案中的檔案。 在某些情況下，您可能不想要或需要發行特定檔案，或您可能想要安裝特定條件為基礎的檔案。 Visual Studio 提供的功能來排除檔案、 將檔案標示為資料檔案或必要條件，以及建立的條件式安裝的檔案群組。  
  
 檔案[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]中受管理應用程式**應用程式檔案**對話方塊中，從存取**發行**頁面**專案設計工具**。  
  
 一開始，沒有名為的單一檔案群組**（必要）**。 您可以建立其他檔案群組，並為其指派的檔案。 您無法變更**下載群組**檔案所需的應用程式執行。 例如，應用程式的.exe 或檔案標示為資料檔案必須屬於**（必要）**群組。  
  
 預設發行狀態檔案的值會標記為**（自動）**。 例如，應用程式的.exe 的發佈狀態**包含 （自動）**預設。  
  
 具有檔案**建置動作**屬性設定為**內容**是指定為應用程式檔案，將會標示為預設包含。 它們可以包含、 排除後，或標示為資料檔案。 例外狀況如下所示：  
  
-   資料檔案，例如 SQL 資料庫 （.mdf 和.mdb） 檔案和 XML 檔案會根據預設標示為資料檔案。  
  
-   當您將加入的參考，如下所示指定組件 （.dll 檔案） 的參考： 如果**複製到本機**是**False**，標示為必要的組件的預設 (**必要條件 (自動）**)，必須先存在於 GAC 中安裝應用程式。 如果**複製到本機**是**True**，做為應用程式組件預設會標記組件 (**包含 （自動）**)，將會複製到應用程式資料夾中進行安裝。 COM 參考會出現在**應用程式檔案**對話方塊方塊中的 （為.ocx 檔案） 只有當其**隔離**屬性設定為**True**。 根據預設，它會包含項目。  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>將檔案新增至應用程式的 [檔案] 對話方塊  
  
1.  選取的資料檔**方案總管 中**。  
  
2.  在 [屬性] 視窗中，變更**建置動作**屬性**內容**值。  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>排除檔案不予 ClickOnce 發行  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**應用程式檔案** 按鈕以開啟**應用程式檔案** 對話方塊。  
  
4.  在**應用程式檔案**對話方塊方塊中，選取您想要排除的檔案。  
  
5.  在**發行狀態**欄位中，選取**排除**從下拉式清單。  
  
### <a name="to-mark-files-as-data-files"></a>若要將檔案標示為資料檔案  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**應用程式檔案** 按鈕以開啟**應用程式檔案** 對話方塊。  
  
4.  在**應用程式檔案**對話方塊方塊中，選取您想要將標記資料的檔案。  
  
5.  在**發行狀態**欄位中，選取**資料檔**從下拉式清單。  
  
### <a name="to-mark-files-as-prerequisites"></a>若要將檔案標示為必要條件  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**應用程式檔案** 按鈕以開啟**應用程式檔案** 對話方塊。  
  
4.  在**應用程式檔案**對話方塊方塊中，選取您想要標記的必要元件的應用程式組件 （.dll 檔案）。 請注意，您的應用程式必須具有應用程式組件的參考，才能讓它出現在清單中。  
  
5.  在**發行狀態**欄位中，選取**必要條件**從下拉式清單。  
  
### <a name="to-add-a-new-file-group"></a>若要加入新的檔案群組  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**應用程式檔案** 按鈕以開啟**應用程式檔案** 對話方塊。  
  
4.  在**應用程式檔案**對話方塊中，選取**群組**欄位以供您想要在新的群組中包含的檔案。  
  
    > [!NOTE]
    >  檔案必須有**建置動作**屬性設定為**內容**檔案名稱會出現在之前**應用程式檔案** 對話方塊。  
  
5.  在**下載群組**欄位中，選取**\<新增...>**從下拉式清單。  
  
6.  在**新增群組**對話方塊中，輸入群組的名稱，然後按一下**確定**。  
  
### <a name="to-add-a-file-to-a-group"></a>將檔案加入至群組  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**應用程式檔案** 按鈕以開啟**應用程式檔案** 對話方塊。  
  
4.  在**應用程式檔案**對話方塊中，選取**群組**欄位以供您想要在新的群組中包含的檔案。  
  
5.  在**下載群組**欄位中，從下拉式清單選取一個群組。  
  
    > [!NOTE]
    >  您無法變更**下載群組**檔案所需的應用程式執行。  
  
## <a name="see-also"></a>請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)