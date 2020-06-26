---
title: 如何-指定哪些檔案是由 ClickOnce 發行 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7ab6d724b40168f84227edb6ccfafc6245c30e0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381778"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>如何：指定哪些檔案是由 ClickOnce 發行
發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，專案中的所有非程式碼檔案都會隨著應用程式一起部署。 在某些情況下，您可能不想要或需要發佈特定檔案，或者您可能想要根據條件來安裝特定檔案。 Visual Studio 提供排除檔案、將檔案標記為資料檔案或必要條件的功能，以及建立用於條件式安裝的檔案群組。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式的檔案會在 [**應用程式檔**] 對話方塊中進行管理，可從 [**專案設計**工具] 的 [**發行**] 頁面存取。

 一開始，有一個名為的單一檔案群組 **（必要）**。 您可以建立其他檔案群組，並將檔案指派給它們。 您無法變更應用程式執行所需之檔案的**下載群組**。 例如，應用程式的 .exe 或標記為資料檔案的檔案必須屬於 **（必要）** 群組。

 檔案的預設發佈狀態值會標記為 **（自動）**。 例如，應用程式的 .exe 預設具有 **[包含（自動）** ] 的發行狀態。

 [**組建動作**] 屬性設為 [**內容**] 的檔案會指定為 [應用程式檔]，且預設會標示為 [已包含]。 這些檔案可以包含、排除或標示為資料檔案。 例外狀況如下：

- SQL Database （*.mdf*和 *.mdb*）檔案和 XML 檔案之類的資料檔案預設會標示為資料檔案。

- 元件（*.dll*檔案）的參考會在您新增參考時指定如下：如果 [**複製到本機**] 為**False**，則預設會將它標示為必要條件元件（必要條件 **（自動）**），必須存在於 GAC 中，才能安裝應用程式。 如果 [**複製到本機**] 為**True**，則元件預設會標示為應用程式元件（**包含（自動）**），而且會在安裝時複製到應用程式資料夾中。 只有當**隔離**的屬性設定為**TRUE**時，COM 參考才會出現在 [**應用程式檔**] 對話方塊中（作為 *.ocx*檔案）。 根據預設，它會包含在內。

### <a name="to-add-files-to-the-application-files-dialog-box"></a>將檔案加入至應用程式檔對話方塊

1. 選取**方案總管**中的資料檔案。

2. 在 [屬性視窗中，將 [**組建動作**] 屬性變更為 [**內容**] 值。

### <a name="to-exclude-files-from-clickonce-publishing"></a>若要從 ClickOnce 發行中排除檔案

1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 按一下 [**應用程式檔**] 按鈕，以開啟 [**應用程式檔**] 對話方塊。

4. 在 [**應用程式檔**] 對話方塊中，選取您想要排除的檔案。

5. 在 [**發行狀態**] 欄位中，從下拉式清單中選取 [**排除**]。

### <a name="to-mark-files-as-data-files"></a>將檔案標記為資料檔案

1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 按一下 [**應用程式檔**] 按鈕，以開啟 [**應用程式檔**] 對話方塊。

4. 在 [**應用程式檔**] 對話方塊中，選取您想要標示為 [資料] 的檔案。

5. 在 [**發行狀態**] 欄位中，從下拉式清單中選取 [**資料檔案**]。

### <a name="to-mark-files-as-prerequisites"></a>將檔案標示為必要條件

1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 按一下 [**應用程式檔**] 按鈕，以開啟 [**應用程式檔**] 對話方塊。

4. 在 [**應用程式檔**] 對話方塊中，選取您要標示為必要條件的應用程式元件（*.dll*檔案）。 請注意，您的應用程式必須具有應用程式元件的參考，才能顯示在清單中。

5. 在 [**發行狀態**] 欄位中，從下拉式清單**中選取 [** 必要條件]。

### <a name="to-add-a-new-file-group"></a>新增檔案群組

1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 按一下 [**應用程式檔**] 按鈕，以開啟 [**應用程式檔**] 對話方塊。

4. 在 [**應用程式檔**] 對話方塊中，選取您想要包含在新群組中之檔案的 [**群組**] 欄位。

    > [!NOTE]
    > 檔案必須將 [**組建動作**] 屬性設定為 [**內容**]，然後檔案名才會出現在 [**應用程式檔**] 對話方塊中。

5. 在 [**下載群組**] 欄位中， **\<New...>** 從下拉式清單中選取。

6. 在 [**新增群組**] 對話方塊中，輸入群組的名稱，然後按一下 **[確定]**。

### <a name="to-add-a-file-to-a-group"></a>將檔案新增至群組

1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。

2. 按一下 [Publish (發行)] **** 索引標籤。

3. 按一下 [**應用程式檔**] 按鈕，以開啟 [**應用程式檔**] 對話方塊。

4. 在 [**應用程式檔**] 對話方塊中，選取您想要包含在新群組中之檔案的 [**群組**] 欄位。

5. 在 [**下載群組**] 欄位中，從下拉式清單中選取一個群組。

    > [!NOTE]
    > 您無法變更應用程式執行所需之檔案的**下載群組**。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)