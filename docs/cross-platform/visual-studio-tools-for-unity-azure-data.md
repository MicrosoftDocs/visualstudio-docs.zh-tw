---
title: "Visual Studio Tools for Unity Azure 逐步解說資料模型 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: e3b6064a3947f57ffcbe6422162c6c72fca0ab21
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="create-data-model-classes"></a>建立資料模型類別

Unity 專案必須包含與 Azure 行動應用程式後端中所建立的資料表對應的資料模型類別。

## <a name="create-the-crashinfo-class"></a>建立 CrashInfo 類別

1. 在 Unity 的根 **Assets** 目錄中，新增一個資料夾並命名為 **Scripts**。 在新的 Scripts 資料夾中，建立另一個新資料夾並命名為 **Data Models**。 這僅供組織使用。

2. 在新的 Data Models 資料夾中，建立新的 C# 指令碼並命名為 **CrashInfo**。

3. 開啟新的 `CrashInfo` 指令碼、刪除任何範本程式碼 (包括類別宣告和 using 陳述式)，並新增下列內容：

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > 若要讓本逐步解說正常運作，資料模型類別名稱必須符合 Azure 行動應用程式後端上所建立的簡易表名稱。

## <a name="create-the-highscoreinfo-class"></a>建立 HighScoreInfo 類別

1. 在 Data Models 資料夾中，建立新的 C# 指令碼並命名為 **HighScoreInfo**。

2. 開啟新的 `HighScoreInfo` 指令碼、刪除任何範本程式碼 (包括類別宣告和 using 陳述式)，並新增下列內容：

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>後續步驟

  * [實作 Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
