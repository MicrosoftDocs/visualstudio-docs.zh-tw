---
title: "Visual Studio Tools for Unity Azure 逐步解說 HeatmapScene | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 472b6d5adae5e23007b9c1aa4d9c75118a94e1cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="heatmapscene-explanation"></a>HeatmapScene 說明

HeatmapScene 包含 **LevelGeometry** prefab 的執行個體。 如此一來，從 Azure 載入的撞車座標就會正確對應至關卡設計。

## <a name="heatmap-script"></a>Heatmap 指令碼

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync` 連線到 Azure 的 CrashInfo 簡易表，並使用 <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx">`ToListAsync`</a> 將其所有項目新增至清單。

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList` 會逐一查看從 Azure 收到的撞車清單，並將每個項目的撞車標記 prefab 具現化。

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

當使用者按下 [清除資料] 按鈕時，會呼叫 `DeleteCrashDataAsync`。 它會逐一查看撞車的本機清單，並針對每個項目呼叫 <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx">`DeleteAsync`</a>。 這會將簡易表中每個項目的 **Deleted** 資料行設定為 **true**。 `ToListAsync` 會忽略這些已刪除的項目。

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>後續步驟

* [LeaderboardScene 說明](visual-studio-tools-for-unity-azure-leaderboardscene.md)