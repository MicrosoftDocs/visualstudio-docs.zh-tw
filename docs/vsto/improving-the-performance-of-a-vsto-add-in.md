---
title: 改善 VSTO 增益集的效能
description: 瞭解如何將您為 Office 應用程式建立的 VSTO 增益集優化，使其快速啟動、關閉、開啟專案及執行其他工作。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83ba2e9cc2cd55b3e3f6362250ffc1e9489b1626
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524441"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>改善 VSTO 增益集的效能
  最佳化您為 Office 應用程式建立的 VSTO 增益集，您可以提供使用者更好的體驗，讓他們快速地啟動、關閉、開啟項目及執行其他工作。 如果是 Outlook 適用的 VSTO 增益集，您還可以減少 VSTO 增益集因為效能不佳而停用的機率。 實作下列策略可以提升 VSTO 增益集的效能：

- [視需要載入 VSTO 增益集](#Load)。

- [使用 Windows Installer 發行 Office 方案](#Publish)。

- [略過功能區反映](#Bypass)。

- [在個別的執行執行緒中執行昂貴的作業](#Perform)。

  如需如何優化 Outlook VSTO 增益集的詳細資訊，請參閱 [效能準則以保持 VSTO 增益集的啟用狀態](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)。

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a> 視需要載入 VSTO 增益集
 您可以設定只在下列情況下才載入 VSTO 增益集：

- 安裝 VSTO 增益集後，使用者第一次啟動應用程式。

- 啟動應用程式後的任何時間點，使用者與 VSTO 增益集的第一次互動。

  例如，當使用者選擇標示為 [ **取得我的資料**] 的自訂按鈕時，VSTO 增益集可能會在工作表中填入資料。 應用程式至少必須載入您的 VSTO 增益集一次，才能讓 [ **取得我的資料** ] 按鈕出現在功能區中。 不過，當使用者下一次啟動應用程式時，不會再次載入 VSTO 增益集。 VSTO 增益集只會在使用者選擇 [取得我的資料]  按鈕時載入。

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>設定 ClickOnce 方案視需要載入 VSTO 增益集

1. 在 [ **方案總管**] 中選擇專案節點。

2. 在功能表列上，選擇 [ **View**  >  **Property Pages**]。

3. 在 [發行]  索引標籤上，選擇 [選項]  按鈕。

4. 在 [發行選項]  對話方塊中，依序選擇 [Office 設定]  清單項目、[視需要載入]  選項，然後再選擇 [確定]  按鈕。

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>設定 Windows Installer 方案視需要載入 VSTO 增益集

1. 在登錄中，將 `LoadBehavior` **_根_\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _增益集識別碼_** 索引鍵的專案設定為 **0x10**。

     如需詳細資訊，請參閱 [VSTO 增益集的登錄專案](../vsto/registry-entries-for-vsto-add-ins.md)。

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>設定方案，在偵錯方案時視需要載入 VSTO 增益集

1. 建立腳本，將 `LoadBehavior` **_根_\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _增益集識別碼_** 索引鍵的專案設定為 **0x10**。

     下列程式碼顯示此指令碼範例。

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. 建立使用指令碼更新登錄的建置後事件。

     下列程式碼顯示的命令字串範例，您可能會加入建置後事件。

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     如需有關如何在 c # 專案中建立組建後事件的詳細資訊，請參閱 [如何：指定 &#40;c&#35;&#41;的組建事件 ](../ide/how-to-specify-build-events-csharp.md)。

     如需如何在 Visual Basic 專案中建立建立後事件的詳細資訊，請參閱 [如何：指定組建事件 &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md)。

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a> 使用 Windows Installer 發佈 Office 方案
 如果您使用 Windows Installer 發行您的方案，則當 VSTO 增益集載入時，Visual Studio 2010 Tools for Office runtime 會略過下列步驟。

- 正在驗證資訊清單結構描述。

- 自動檢查更新。

- 驗證部署資訊清單的數位簽章。

  > [!NOTE]
  > 如果您將 VSTO 增益集部署到使用者電腦上的安全位置，就不需要這個方法。

  如需詳細資訊，請參閱 [使用 Windows Installer 部署 Office 方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> 略過功能區反映
 如果您使用建立解決方案 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] ，請確定您的使用者在部署方案時，已安裝最新版的 Visual Studio 2010 Tools For Office runtime。 舊版的 VSTO 執行時間會反映到方案元件中，以找出功能區自訂專案。 此程序會使得 VSTO 增益集載入的速度更加緩慢。

 或者，您可以防止任何版本的 Visual Studio 2010 Tools for Office runtime 使用反映來識別功能區自訂專案。 若要遵循此策略，請覆寫 `CreateRibbonExtensibility` 方法，並明確傳回功能區物件。 如果 VSTO 增益集未包含任何功能區自訂，則會在 `null` 方法內傳回。

 下列範例會根據欄位的值傳回功能區物件。

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> 在個別的執行執行緒中執行耗費資源的作業
 請考慮在不同的執行緒中執行耗時的工作 (例如需長時間執行的工作、資料庫連接或其他類型的網路呼叫)。 如需詳細資訊，請參閱 [Office 中的執行緒支援](../vsto/threading-support-in-office.md)。

> [!NOTE]
> 所有呼叫 Office 物件模型的程式碼，都必須在主執行緒中執行。

## <a name="see-also"></a>另請參閱

- [要求-載入 VSTO 增益集](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [在 Office 增益集中延遲載入 CLR](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [使用 Visual Studio 建立適用於 Office 的 VSTO 增益集](create-vsto-add-ins-for-office-by-using-visual-studio.md)