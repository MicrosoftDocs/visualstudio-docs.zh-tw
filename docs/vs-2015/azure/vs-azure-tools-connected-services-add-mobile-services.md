---
title: 在 Visual Studio 中使用已連接服務加入行動服務 |Microsoft Docs
description: 使用 Visual Studio 加入已連接服務 對話方塊加入行動服務
documentationcenter: na
author: ghogen
manager: douge
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 1679f8e20c4516ab64c4358229b4eec6ab5029ba
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001985"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>使用 Visual Studio 已連接服務加入行動服務
使用 Visual Studio 2015，您可以連接到 Azure 行動服務使用**加入已連接服務**對話方塊。 您可以從任何連線C#用戶端應用程式、 任何 JavaScript 應用程式或跨平台 Cordova 應用程式。 連接之後，您可以建立和存取資料、 建立自訂 Api 和排程的工作，或加入推播通知的支援。  已連線的服務作業會加入所有適當的參考和連接程式碼。 您也可以利用內建支援各種熱門身分識別配置，例如 Azure AD 中，驗證的 Facebook、 Twitter 和 Microsoft 帳戶。

## <a name="supported-project-types"></a>支援的專案類型
> [!NOTE]
> 在 Visual Studio 2015 中，不支援將 Azure 行動服務加入至 Windows 通用 (Windows 10) 的專案中，藉由使用 [加入已連接服務] 對話方塊。 您可以新增 Azure 行動服務安裝適當的封裝，使用 NuGet 封裝管理員為您的專案。
> 
> 

您可以使用已連接服務對話方塊連接到 Azure 行動服務中的下列專案類型。

* .NET Windows 8.1 市集、 電話和通用應用程式專案
* JavaScript Windows 8.1 市集、 電話和通用應用程式專案
* 使用 Visual Studio Tools for Apache Cordova 建立的專案

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>連接到 Azure 行動服務，使用 [加入已連接服務] 對話方塊
1. 請確定您有 Azure 帳戶。 如果您沒有 Azure 帳戶，您可以申請[免費試用](http://go.microsoft.com/fwlink/?LinkId=518146)。
2. 開啟**加入已連接服務** 對話方塊。
   
   * .NET 應用程式，在 Visual Studio 中開啟您的專案，開啟操作功能表**參考**方案總管] 中的節點，然後選擇 [**加入已連接服務**
     
        ![連接到 Azure 行動服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Apache Cordova 應用程式專案，請在 Visual Studio 中開啟您的專案，在 [方案總管] 中，開啟專案節點的操作功能表，然後選擇**加入已連接服務**。
3. 在 **加入已連接服務**對話方塊方塊中，選擇**Azure 行動服務**，然後選擇 **設定**按鈕。 系統可能會提示您登入 Azure，如果您還尚未這麼做。
   
    ![新增 Azure 行動服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. 在  **Azure 行動服務**對話方塊方塊中，如果有的話，請選擇現有行動服務。 如果您需要建立新的 Azure 行動服務，請依照下列程序來執行這項操作。 否則，請跳至下一個步驟。
   
    若要建立新的行動服務帳戶：
   
   1. 選擇 建立服務 * * 對話方塊底部的連結。
       ![加入新的行動裝置已連接的服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. 在 [**建立行動服務**] 對話方塊中，您可以選擇 JavaScript 後端行動服務或從的.NET 後端行動服務**Runtime**下拉式清單。 
      
       ![建立行動服務](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)
      
       JavaScript 後端服務既簡單又強大。 如果您建立 JavaScript 後端行動服務時，伺服器端 JavaScript 程式碼儲存在雲端，但您可以使用 伺服器總管 或 Azure 管理入口網站來編輯伺服器指令碼。 
      
       .NET 後端行動服務可讓您的完整威力與 Web API 和 Entity Framework 的彈性。 如果您建立.NET 後端行動服務，是為您建立專案，並新增至您的解決方案。 
   3. 選擇**地區**您想要行動服務中，然後輸入伺服器的 使用者名稱和密碼。
   4. 您輸入所有必要的資訊之後，請選擇**建立** 按鈕來建立行動服務。
   5. 新的行動服務時，應該出現在 服務 清單上，在**Azure 行動服務** 對話方塊。 在清單中選擇新的行動服務，然後選擇**新增** 按鈕，將服務新增至您的專案。
5. 檢閱開始使用 頁面出現，並了解您的專案修改方式。 每當您新增已連接的服務時，使用者入門 頁面會出現在您的瀏覽器。 您可以檢閱建議的後續步驟和程式碼範例，或切換至 [發生什麼情形] 頁面以查看哪些參考已加入至您的專案，以及如何修改您的程式碼和組態檔。
6. 使用程式碼範例做為指南，開始撰寫程式碼以存取您的行動服務 ！

## <a name="how-your-project-is-modified"></a>您的專案修改方式
Visual Studio 修改專案的方式需視專案類型而定。 針對C#用戶端應用程式，請參閱[發生什麼情形 –C#專案](http://go.microsoft.com/fwlink/p/?LinkId=513119)。 JavaScript 用戶端應用程式，請參閱[發生什麼情形 – JavaScript 專案](http://go.microsoft.com/fwlink/p/?LinkId=513120)。 針對 Cordova 應用程式，請參閱[發生什麼情形 – Cordova 專案](http://go.microsoft.com/fwlink/p/?LinkId=513116)。

## <a name="next-steps"></a>後續步驟
詢問問題並取得協助： 

* [MSDN 論壇︰ Azure 行動服務](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Microsoft Azure 團隊部落格上的 azure 行動服務](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure.microsoft.com 的 azure 行動服務](https://azure.microsoft.com/services/mobile-services/)
* [Azure.microsoft.com 上的 azure 行動服務文件](https://azure.microsoft.com/documentation/services/mobile-services/)

