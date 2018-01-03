---
title: "Visual Studio Tools for Unity Azure 逐步解說連線 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: cb2ce447f21231b98d6464824ba7d088fee16cce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-client-connection"></a>測試用戶端連線

現在已建立單一 AzureMobileServiceClient，接下來將測試用戶端連線。

## <a name="create-the-testclientconnection-script"></a>建立 TestClientConnection 指令碼

1. 在 Unity 的 **Scripts** 資料夾中，建立新的 C# 指令碼並命名為 **TestClientConnection**。

2. 在 Visual Studio 中開啟指令碼、刪除任何範本程式碼，並新增下列內容：

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. 在 Unity 的 [GameObject] 功能表中，選取 [GameObject] > [建立空白]，在 Unity 場景中建立空白 GameObject。 將它重新命名為 **TestClientConnection**。

4. 將 TestClientConnection 指令碼從 Unity 的 [專案] 視窗**拖曳**至 [階層] 視窗中的 TestClientConnection GameObject 上。

5. 在 Unity 功能表中，選取 [檔案] > [另存場景為...]。將場景命名為**用戶端連線測試**，然後按一下 [儲存]。

5. 在 Unity 中，按一下 [播放] 按鈕，並觀察 [主控台] 視窗。 確認沒有任何判斷提示失敗。

6. 在 Azure 入口網站上開啟 CrashInfo 簡易表。 它現在應該會有 **(1, 2, 3)** 的 **X,Y,Z** 座標項目，並在 **deleted** 資料行中有 **true** 值。 每次執行測試，都會在資料表中新增一個具有相同值但唯一識別碼的項目。

  ![簡易表項目](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>後續步驟
* [匯入範例遊戲資產](visual-studio-tools-for-unity-azure-game-assets.md)。
