---
title: "Visual Studio Tools for Unity Azure 逐步解說 Mobile Client | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 451b4f1f2580a55077bf3fc6a9ad3f16a2afaf0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>實作 Azure MobileServiceClient

Azure Mobile Client SDK 的中心是允許存取行動應用程式後端的 <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a>。

## <a name="locate-the-url-of-the-mobile-app-backend"></a>找出行動應用程式後端的 URL

`MobileServiceClient` 建構函式以行動應用程式 URL 作為參數，因此請先找出此 URL，再繼續進行。

1. 在 Azure 入口網站中，按一下 [應用程式服務] 按鈕。

    ![按一下 [應用程式服務]](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. 按一下您的行動應用程式項目。

    ![按一下行動應用程式](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. 複製您行動應用程式後端的 URL。

    ![複製 URL](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>建立單一 MobileServiceClient

由於只能有一個 `MobileServiceClient` 執行個體，因此本逐步解說會使用此單一模式的變化。

1. 在 Unity 專案的 **Assets/Scripts** 目錄中，建立新的 C# 指令碼並命名為 **AzureMobileServiceClient**。

2. 開啟 `AzureMobileServiceClient` 指令碼，並刪除任何現有的範本程式碼，包括 using 陳述式和類別宣告。

3. 加入下列程式碼：

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > 如果 IntelliSense 無法辨識 Microsoft.WindowsAzure 命名空間，請檢查您是否已完成[準備開發環境]()一節中的所有步驟。

4. 在上述程式碼中，以您行動應用程式後端的 URL 取代 `MOBILE_APP_URL`。

## <a name="next-step"></a>後續步驟

* [更新 Unity Mono 安全性存放區](visual-studio-tools-for-unity-azure-security.md)
