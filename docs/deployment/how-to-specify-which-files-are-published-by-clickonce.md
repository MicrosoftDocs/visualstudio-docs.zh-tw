---
title: 指定要發佈 (ClickOnce) 的檔案
description: 瞭解如何排除檔案、將檔案標示為資料檔案或必要條件，以及建立 ClickOnce 應用程式的條件式安裝群組。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d093438dc30bee08abbc45c6cf3c2555fbe208c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887480"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>如何：指定哪些檔案是由 ClickOnce 發行
發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，專案中的所有非程式碼檔案都會隨著應用程式一起部署。 在某些情況下，您可能不想要或不需要發佈特定檔案，或者您可能會想要根據條件安裝某些檔案。 Visual Studio 提供排除檔案、將檔案標示為資料檔案或必要條件，以及建立條件式安裝的檔案群組的功能。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式的檔案會在 [**應用程式檔**] 對話方塊中進行管理，您可以從 [**專案設計** 工具] 的 [**發行**] 頁面存取此對話方塊。

 一開始，有一個名為 **(必要)** 的單一檔案群組。 您可以建立其他檔案群組，並將檔案指派給它們。 您無法變更應用程式執行所需之檔案的 **下載群組** 。 例如，應用程式的 .exe 或標示為資料檔案的檔案必須屬於 **(必要的)** 群組。

 檔案的預設發佈狀態值會以 **(Auto)** 標記。 例如，根據預設，應用程式的 .exe 有 [ **包含 (自動)** 的 [發行] 狀態。

 將 [ **組建動作** ] 屬性設定為 [ **內容** ] 的檔案會指定為 [應用程式檔]，並且預設會標示為 [已包含]。 它們可以包含、排除或標示為資料檔案。 例外狀況如下：

- 資料檔案（例如 SQL Database (*.mdf* 和 *.mdb*) 檔案和 XML 檔案預設會標示為資料檔案。

- 當您加入參考時，會將元件 (*.dll* 檔案) 的參考指定如下：如果 [ **複製到本機** ] 為 **False**，則預設會將它標示為必要條件元件 (必要條件 **(自動)**) 必須在安裝應用程式之前存在於 GAC 中。 如果 [ **複製到本機** ] 為 **True**，則預設會將元件標示為應用程式元件 (**包含 (自動)**) ，並且會在安裝時複製到應用程式資料夾。 COM 參考將會出現在 [**應用程式檔**] 對話方塊中， (為 .ocx 檔案，只有在其 **隔離** 的屬性設為 **True** 時才會) *。* 依預設，它會包含在內。

### <a name="to-add-files-to-the-application-files-dialog-box"></a>將檔案加入至 [應用程式檔] 對話方塊

1. 在 **方案總管** 中選取資料檔案。

2. 在 [屬性視窗中，將 [ **組建動作** ] 屬性變更為 [ **內容** ] 值。

### <a name="to-exclude-files-from-clickonce-publishing"></a>從 ClickOnce 發行中排除檔案

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **應用程式檔** ] 按鈕，以開啟 [ **應用程式檔** ] 對話方塊。

4. 在 [ **應用程式檔** ] 對話方塊中，選取您要排除的檔案。

5. 在 [ **發行狀態** ] 欄位中，從下拉式清單中選取 [ **排除** ]。

### <a name="to-mark-files-as-data-files"></a>將檔案標示為資料檔案

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **應用程式檔** ] 按鈕，以開啟 [ **應用程式檔** ] 對話方塊。

4. 在 [ **應用程式檔** ] 對話方塊中，選取您要標示為數據的檔案。

5. 在 [ **發行狀態** ] 欄位中，從下拉式清單中選取 [ **資料檔案** ]。

### <a name="to-mark-files-as-prerequisites"></a>將檔案標示為必要條件

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **應用程式檔** ] 按鈕，以開啟 [ **應用程式檔** ] 對話方塊。

4. 在 [ **應用程式檔** ] 對話方塊中，選取您要標示為必要條件的應用程式元件 (*.dll* 檔) 。 請注意，您的應用程式必須具有應用程式元件的參考，才能讓它出現在清單中。

5. 在 [ **發行狀態** ] 欄位中 **，從下拉式清單中選取** [必要條件]。

### <a name="to-add-a-new-file-group"></a>若要加入新的檔案群組

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **應用程式檔** ] 按鈕，以開啟 [ **應用程式檔** ] 對話方塊。

4. 在 [ **應用程式檔** ] 對話方塊中，選取您要包含在新群組中之檔案的 [ **群組** ] 欄位。

    > [!NOTE]
    > 檔案必須將 [ **組建動作** ] 屬性設定為 [ **內容** ]，才會在 [ **應用程式檔** ] 對話方塊中顯示檔案名。

5. 在 [ **下載群組** ] 欄位中， **\<New...>** 從下拉式清單中選取。

6. 在 [ **新增群組** ] 對話方塊中，輸入群組的名稱，然後按一下 **[確定]**。

### <a name="to-add-a-file-to-a-group"></a>將檔案新增至群組

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **應用程式檔** ] 按鈕，以開啟 [ **應用程式檔** ] 對話方塊。

4. 在 [ **應用程式檔** ] 對話方塊中，選取您要包含在新群組中之檔案的 [ **群組** ] 欄位。

5. 在 [ **下載群組** ] 欄位中，從下拉式清單中選取群組。

    > [!NOTE]
    > 您無法變更應用程式執行所需之檔案的 **下載群組** 。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)