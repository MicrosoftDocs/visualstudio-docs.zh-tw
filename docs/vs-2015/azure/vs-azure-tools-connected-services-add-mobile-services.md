---
title: 使用已連線的服務新增行動服務
description: 使用 [Visual Studio 新增已連線的服務] 對話方塊來新增行動服務
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300185"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>使用 Visual Studio 已連線的服務新增行動服務
使用 Visual Studio 2015，您可以使用 [**加入已連接服務**] 對話方塊連接到 Azure 行動服務。 您可以從任何C#用戶端應用程式、任何 JavaScript 應用程式或跨平臺 Cordova 應用程式進行連接。 連接之後，您可以建立和存取資料、建立自訂 Api 和排程工作，或新增推播通知的支援。  「已連接服務」作業會新增所有適當的參考和連接程式碼。 您也可以利用各種熱門身分識別配置（例如 Azure AD、Facebook、Twitter 和 Microsoft 帳戶）的內建驗證支援。

## <a name="supported-project-types"></a>支援的專案類型
> [!NOTE]
> 在 Visual Studio 2015 中，不支援使用 [新增已連線的服務] 對話方塊將 Azure 行動服務加入至 Windows 通用（Windows 10）專案。 您可以使用專案的 NuGet 套件管理員來安裝適當的套件，藉以新增 Azure 行動服務。
>
>

您可以使用 [已連線的服務] 對話方塊來連接到下列專案類型中的 Azure 行動服務。

* .NET Windows 8.1 存放區、電話和通用應用程式專案
* JavaScript Windows 8.1 存放區、電話和通用應用程式專案
* 使用 Visual Studio Tools Apache Cordova 建立的專案

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>使用 [新增已連線的服務] 對話方塊連接到 Azure 行動服務
1. 請確定您有 Azure 帳戶。 如果您沒有 Azure 帳戶，您可以註冊[免費試用](https://go.microsoft.com/fwlink/?LinkId=518146)。
2. 開啟 [**加入已連線的服務**] 對話方塊。

   * 針對 .NET 應用程式，請在 Visual Studio 中開啟您的專案，在方案總管中開啟 [**參考**] 節點的操作功能表，然後選擇 [**加入已連接服務**]。

        ![連接到 Azure 行動服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * 針對 Apache Cordova 應用程式專案，請在 Visual Studio 中開啟您的專案，在方案總管中開啟專案節點的內容功能表，然後選擇 [**加入已連接服務**]。
3. 在 [加入已連接服務] 對話方塊中，選擇 [Azure 行動服務]，然後選擇 [設定] 按鈕。 如果您尚未登入 Azure，系統可能會提示您這樣做。

    ![新增 Azure 行動服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. 在 [Azure 行動服務] 對話方塊中，選擇現有行動服務 (如果有的話)。 如果您需要建立新的 Azure 行動服務，請遵循下列程式來執行此動作。 否則，請跳至下一個步驟。

    若要建立新的行動服務帳戶：

   1. 選擇對話方塊底部的 [建立服務] 連結。
       ![新增行動聯機服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. 在 [**建立行動服務**] 對話方塊中，您可以從 [**運行**時間] 下拉式清單中選擇 JavaScript 後端行動服務或 .net 後端行動服務。

       ![建立行動服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       JavaScript 後端服務既簡單又強大。 如果您建立 JavaScript 後端行動服務，伺服器端 JavaScript 程式碼會儲存在雲端中，但是您可以使用 [伺服器總管] 或 Azure 管理入口網站來編輯伺服器指令碼。

       .NET 後端行動服務可提供您 Web API 和 Entity Framework 的完整功能和彈性。 如果您建立 .NET 後端行動服務，就會為您建立專案，並將其新增至您的方案。
   3. 選擇您想要行動服務的 [區域]，然後輸入伺服器的使用者名稱和密碼。
   4. 輸入所有必要資訊之後，請選擇 [建立] 按鈕來建立行動服務。
   5. 新的行動服務應該會出現在 [ **Azure 行動服務**] 對話方塊的服務清單中。 在清單中選擇新的行動服務，然後選擇 [加入] 按鈕，將服務加入至您的專案。
5. 查看出現的 [開始使用] 頁面，並瞭解您的專案修改方式。 每當您加入連接的服務時，[快速入門] 頁面會出現在瀏覽器中。 您可以檢閱建議的後續步驟和程式碼範例，或切換至 [發生什麼情形] 頁面，查看已加入到您專案中的參考，以及您的程式碼和組態檔有何修改。
6. 使用程式碼範例做為指南，開始撰寫程式碼以存取您的行動服務！

## <a name="how-your-project-is-modified"></a>您的專案修改方式
Visual Studio 修改專案的方式取決於專案類型。 針對C#用戶端應用程式，請參閱[發生什麼事C# –專案](https://go.microsoft.com/fwlink/p/?LinkId=513119)。 針對 JavaScript 用戶端應用程式，請參閱[發生什麼事-JavaScript 專案](https://go.microsoft.com/fwlink/p/?LinkId=513120)。 針對 Cordova 應用程式，請參閱[發生什麼事– Cordova 專案](https://go.microsoft.com/fwlink/p/?LinkId=513116)。

## <a name="next-steps"></a>後續步驟
提出問題並取得協助：

* [MSDN 論壇： Azure 行動服務](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Microsoft Azure 小組 Blog 中的 Azure 行動服務](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure.microsoft.com 上的 Azure 行動服務](https://azure.microsoft.com/services/mobile-services/)
* [Azure.microsoft.com 上的 Azure 行動服務檔](https://azure.microsoft.com/documentation/services/mobile-services/)
