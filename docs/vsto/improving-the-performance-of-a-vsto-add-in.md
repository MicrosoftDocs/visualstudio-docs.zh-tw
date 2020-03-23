---
title: 提高 VSTO 外接程式的性能
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
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416545"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>提高 VSTO 外接程式的性能
  最佳化您為 Office 應用程式建立的 VSTO 增益集，您可以提供使用者更好的體驗，讓他們快速地啟動、關閉、開啟項目及執行其他工作。 如果是 Outlook 適用的 VSTO 增益集，您還可以減少 VSTO 增益集因為效能不佳而停用的機率。 實作下列策略可以提升 VSTO 增益集的效能：

- [按需載入 VSTO 載入項](#Load)。

- [使用 Windows 安裝程式 發佈 Office 解決方案](#Publish)。

- [旁路帶反射](#Bypass)。

- [在單獨的執行執行緒中執行昂貴的操作](#Perform)。

  有關如何優化 Outlook VSTO 外接程式的詳細資訊，請參閱保持[VSTO 外接程式啟用的性能條件](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)。

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>按需載入 VSTO 載入項
 您可以設定只在下列情況下才載入 VSTO 增益集：

- 安裝 VSTO 增益集後，使用者第一次啟動應用程式。

- 啟動應用程式後的任何時間點，使用者與 VSTO 增益集的第一次互動。

  例如，當使用者選擇標記為"**獲取我的資料**"的自訂按鈕時，您的 VSTO 外接程式可能會使用資料填充工作表。 應用程式必須至少載入一次 VSTO 外接程式，以便 **"獲取我的資料**"按鈕可以顯示在功能區中。 但是，當使用者下次啟動應用程式時，VSTO 外接程式不會再次載入。 VSTO 增益集只會在使用者選擇 [取得我的資料] **** 按鈕時載入。

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>設定 ClickOnce 方案視需要載入 VSTO 增益集

1. 在 [ **方案總管**] 中選擇專案節點。

2. 在功能表列上，選擇 **"查看** > **屬性頁**"。

3. 在 [發行] **** 索引標籤上，選擇 [選項] **** 按鈕。

4. 在 [發行選項] **** 對話方塊中，依序選擇 [Office 設定] **** 清單項目、[視需要載入] **** 選項，然後再選擇 [確定] **** 按鈕。

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>設定 Windows Installer 方案視需要載入 VSTO 增益集

1. 在註冊表`LoadBehavior`中，將**_根_\\[軟體]Microsoft_Office_應用程式名稱_\Addins\\外接程式 ID**金鑰的條目設置為**0x10**。

     有關詳細資訊，請參閱[VSTO 載入項的登錄機碼](../vsto/registry-entries-for-vsto-add-ins.md)。

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>設定方案，在偵錯方案時視需要載入 VSTO 增益集

1. 創建一個腳本，將`LoadBehavior`**_根_[軟體]Microsoft_Office\\_應用程式名稱_[Addins\\外接程式 ID**金鑰的條目集**0x10**。

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

     有關如何在 C# 專案中創建生成後事件的資訊，請參閱[：&#40;C&#35;&#41;指定建置事件](../ide/how-to-specify-build-events-csharp.md)。

     有關如何在 Visual Basic 專案中創建生成後事件的資訊，請參閱[如何：指定 &#40;視覺化基本&#41;的建置事件](../ide/how-to-specify-build-events-visual-basic.md)。

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>使用 Windows 安裝程式發佈 Office 解決方案
 如果使用 Windows 安裝程式發佈解決方案，則當 VSTO 外接程式載入時，適用于 Office 運行時的 Visual Studio 2010 工具會繞過以下步驟。

- 正在驗證資訊清單結構描述。

- 自動檢查更新。

- 驗證部署資訊清單的數位簽章。

  > [!NOTE]
  > 如果將 VSTO 外接程式部署到使用者電腦上的安全位置，則此方法不是必需的。

  有關詳細資訊，請參閱使用[Windows 安裝程式部署 Office 解決方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>旁路功能區反射
 如果使用 生成[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]解決方案，請確保使用者在部署解決方案時安裝了最新版本的 Visual Studio 2010 Office 運行時工具。 較舊版本的 VSTO 運行時反映在解決方案程式集中，以查找功能區自訂項。 此程序會使得 VSTO 增益集載入的速度更加緩慢。

 作為替代方法，您可以防止任何版本的 Visual Studio 2010 Office 運行時工具使用反射來標識功能區自訂項。 要遵循此策略，`CreateRibbonExtensibility`請重寫 該方法，並顯式返回功能區物件。 如果 VSTO 外接程式不包含任何功能區自訂項，請返回`null`方法內部。

 下面的示例基於欄位的值返回功能區物件。

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>在單獨的執行執行緒中執行昂貴的操作
 請考慮在不同的執行緒中執行耗時的工作 (例如需長時間執行的工作、資料庫連接或其他類型的網路呼叫)。 有關詳細資訊，請參閱[Office 中的執行緒支援](../vsto/threading-support-in-office.md)。

> [!NOTE]
> 所有呼叫 Office 物件模型的程式碼，都必須在主執行緒中執行。

## <a name="see-also"></a>另請參閱

- [需求載入 VSTO 載入項](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [在 Office 增益集中延遲載入 CLR](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [使用 Visual Studio 建立適用於 Office 的 VSTO 增益集](create-vsto-add-ins-for-office-by-using-visual-studio.md)
