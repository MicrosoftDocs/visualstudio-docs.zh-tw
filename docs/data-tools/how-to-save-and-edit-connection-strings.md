---
title: "如何： 儲存和編輯連接字串 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 4a7482c269cd978d2c1848c896985b1194797e42
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-save-and-edit-connection-strings"></a>如何：儲存和編輯連接字串
Visual Studio 應用程式中的連接字串可以儲存在應用程式組態檔 （也稱為應用程式設定），或硬式編碼直接在您的應用程式中。 將連接字串儲存至應用程式組態檔，可簡化應用程式維護工作。 如果需要變更連接字串，則您可以在應用程式設定檔中更新它 (而不需要在原始程式碼中變更它並重新編譯應用程式)。

在連接字串內儲存敏感性資訊 (如密碼) 會影響應用程式的安全性。 不會加密或模糊化儲存至應用程式組態檔的連接字串，因此，可能會有人存取該檔案並檢視其內容。 使用 Windows 整合式安全性是控制資料庫存取的更安全方式。

如果您未選擇使用 Windows 整合式安全性，而且您的資料庫需要使用者名稱和密碼，則可以透過連接字串省略它們，但是，您的應用程式還是需要提供此資訊才能順利連接至資料庫。 例如，您可以建立提示使用者輸入此資訊的對話方塊，並在執行階段動態建置連接字串。 如果在進出資料庫的資訊中攔截到該資訊，則安全性可能還是有問題。 如需詳細資訊，請參閱[保護連線資訊](/dotnet/framework/data/adonet/protecting-connection-information)。

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>若要儲存資料來源組態精靈中的連接字串
在**資料來源組態精靈**，選取要將連接儲存在連接字串儲存到應用程式組態檔 頁面上的選項。

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>將連接字串直接儲存至應用程式設定
- 在方案總管] 中，按兩下 [我的專案圖示 (Visual Basic) 或屬性] 圖示 (C#) 以開啟 [專案設計工具。
- 選取 [設定] 索引標籤。
- 輸入連接字串的名稱。 在程式碼中存取連接字串時，請參考此名稱。
- 將類型設定為 （連接字串）。
- 將保留範圍設定為應用程式。
- 在 [值] 欄位中，輸入您的連接字串，或按一下省略符號 （...） 按鈕，以開啟 [連接屬性] 對話方塊來建立連接字串值欄位中。  

## <a name="editing-connection-strings-stored-in-application-settings"></a>編輯應用程式設定中儲存的連接字串
您可以修改連接資訊儲存在應用程式設定中使用 專案設計工具。  

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>編輯應用程式設定中儲存的連接字串
- 在方案總管] 中，按兩下 [我的專案圖示 (Visual Basic) 或屬性] 圖示 (C#) 以開啟 [專案設計工具。
- 選取 [設定] 索引標籤。
- 找出您想要編輯選取的文字值欄位中的連接。
- 編輯值 欄位中的連接字串，或按一下省略符號 （...） 按鈕來編輯您的連接與連接屬性 對話方塊的 值 欄位中。  

## <a name="editing-connection-strings-for-datasets"></a>編輯資料集的連接字串
您可以修改資料集內的每個 TableAdapter 的連接資訊。  

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>若要編輯資料集內的 TableAdapter 的連接字串
- 在 方案總管 中，按兩下 資料集 （.xsd 檔案） 具有您想要編輯的連接。
- 選取具有您想要編輯的連接查詢的 TableAdapter。
- 在 [屬性] 視窗中，展開連接節點。
- 若要快速修改連接字串，編輯 ConnectionString 屬性，或按一下 連接屬性上的向下箭號並選擇 新的連接。

## <a name="security"></a>安全性
在連接字串內儲存敏感性資訊 (如密碼) 會影響應用程式的安全性。 使用 Windows 整合式安全性是控制資料庫存取的更安全方式。
如需詳細資訊，請參閱[保護連線資訊](/dotnet/framework/data/adonet/protecting-connection-information)。
  
## <a name="see-also"></a>請參閱
[加入連接](../data-tools/add-new-connections.md)