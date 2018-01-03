---
title: "Visual Studio Tools for Unity Azure 逐步解說 RaceScene | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7dc57628774624975cc6ede5bd241f322472bfe6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="racescene-explanation"></a>RaceScene 說明

RaceScene 使用 Unity [標準資產](https://www.assetstore.unity3d.com/en/#!/content/32351)來撰寫基本賽車遊戲和關卡。 在本節中，將會依相關 GameObject 及其指令碼列於 RaceScene 階層架構中的順序來進行說明，如下列螢幕擷取畫面所示。

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

**MultipurposeCameraRig** 來自 **Cameras** 標準資產套件。 其檢查屬性已經過調整，會遵循適當的速度來追蹤車輛。

## <a name="levelgeometry"></a>LevelGeometry

LevelGeometry prefab 是用於組織的空 GameObject。 其子 GameObject 組成可進行遊戲的空間。 所有樓層、牆壁、坡道和障礙物都是從 **Prototyping** 標準資產套件的 prefab 建置而成。

**請注意**，為了讓物件可以接受 Azure 中記錄的撞車測試，必須套用 [Wall] 標籤。

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Car

**Car** prefab 來自 **Vehicles** 標準資產套件。 唯一的修改是新增 **RecordCrashInfo** 指令碼元件。

### <a name="recordcrashinfo"></a>RecordCrashInfo

此指令碼會檢查 `OnCollisionEnter` 中是否有撞車並記錄到清單中。 `crashRecordingCooldown` 和 `crashRecordingMinVelocity` 會限制遊戲認定撞車的情況，以保留相關的資料集。

引發 `RaceFinished` 事件時，`UploadNewCrashDataAsync` 會將清單中的每起撞車傳送至 Azure 的 CrashInfo 簡易表。

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>checkpoints

關卡包含四個具有**檢查點**指令碼元件的 GameObject。 檢查點可確保玩家不會在賽車場繞錯方向而無法完成比賽，同時也會偵測玩家何時完成比賽。 這是叫用 `RaceFinished` 事件的位置。

## <a name="invisible-collision"></a>不可見的碰撞

已停用其 MeshRenderer 元件的標準基本 Cube 可作為不可見的碰撞，以便限制玩家的行動範圍。 此外，會套用 **Bouncy** 物理材料，以確保飛車以安全的方式彈出不可見的牆，並防止玩家撞到不可見的牆、從上滑下並降落在可見的牆上。

## <a name="recordhighscore"></a>RecordHighScore

此指令碼會檢查玩家是否已刷新高分記錄。 如果是，則會顯示 `enterNamePopup`，讓玩家輸入其名稱並按一下 [送出]。

一旦送出玩家名稱，就會呼叫 `UploadNewHighScoreAsync` 並將新的高分記錄傳送至 Azure 的 HighScoreInfo 簡易表。

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>後續步驟

* [HeatmapScene 說明](visual-studio-tools-for-unity-azure-heatmapscene.md)。
