---
title: 提升 VSTO 增益集的效能
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc4a65a0b09a706eebad04c90e1779d00c7f3801
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937279"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>提升 VSTO 增益集的效能
  最佳化您為 Office 應用程式建立的 VSTO 增益集，您可以提供使用者更好的體驗，讓他們快速地啟動、關閉、開啟項目及執行其他工作。 如果是 Outlook 適用的 VSTO 增益集，您還可以減少 VSTO 增益集因為效能不佳而停用的機率。 實作下列策略可以提升 VSTO 增益集的效能：

- [視需要載入 VSTO 增益集](#Load)。

- [使用 Windows Installer 發行 Office 方案](#Publish)。

- [略過功能區反映](#Bypass)。

- [在不同的執行緒中執行耗費資源的作業](#Perform)。

  如需如何最佳化 Outlook VSTO 增益集的詳細資訊，請參閱[保持 VSTO 增益集已啟用的效能準則](http://go.microsoft.com/fwlink/?LinkID=266503)。

##  <a name="Load"></a> 視需要載入 VSTO 增益集
 您可以設定只在下列情況下才載入 VSTO 增益集：

- 安裝 VSTO 增益集後，使用者第一次啟動應用程式。

- 啟動應用程式後的任何時間點，使用者與 VSTO 增益集的第一次互動。

  例如，您 VSTO 增益集可能會在工作表填入資料當使用者選擇標示為自訂按鈕**取得我的資料**。 應用程式必須載入 VSTO 增益集在至少一次，讓**取得我的資料**按鈕才會出現在功能區中。 不過，VSTO 增益集不會再次載入當使用者啟動應用程式在下一次。 VSTO 增益集只會在使用者選擇 [取得我的資料]  按鈕時載入。

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>設定 ClickOnce 方案視需要載入 VSTO 增益集

1.  在 [ **方案總管**] 中選擇專案節點。

2.  在功能表列上選擇 [檢視 ] > [屬性頁]。

3.  在 [發行]  索引標籤上，選擇 [選項]  按鈕。

4.  在 [發行選項]  對話方塊中，依序選擇 [Office 設定]  清單項目、[視需要載入]  選項，然後再選擇 [確定]  按鈕。

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>設定 Windows Installer 方案視需要載入 VSTO 增益集

1.  在登錄中，設定`LoadBehavior`項目**_根_\Software\Microsoft\Office\\_ApplicationName_\Addins\\ _增益集 ID_** 機碼**0x10**。

     如需詳細資訊，請參閱 < [VSTO 增益集的登錄項目](../vsto/registry-entries-for-vsto-add-ins.md)。

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>設定方案，在偵錯方案時視需要載入 VSTO 增益集

1.  建立設定的指令碼`LoadBehavior`項目**_根_\Software\Microsoft\Office\\_ApplicationName_\Addins\\ _增益集 ID_** 機碼**0x10**。

     下列程式碼顯示此指令碼範例。

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2.  建立使用指令碼更新登錄的建置後事件。

     下列程式碼顯示的命令字串範例，您可能會加入建置後事件。

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     如需如何建立建置後事件中的資訊C#專案，請參閱[如何：指定建置事件&#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md)。

     如需如何在 Visual Basic 專案中建立建置後事件的資訊，請參閱[How to:指定建置事件&#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md)。

##  <a name="Publish"></a> 使用 Windows Installer 發行 Office 方案
 如果您使用 Windows Installer 發行方案，Visual Studio 2010 Tools for Office 執行階段略過下列步驟，VSTO 增益集載入時也一樣。

- 正在驗證資訊清單結構描述。

- 自動檢查更新。

- 驗證部署資訊清單的數位簽章。

  > [!NOTE]
  >  這個方法如果不需要將您 VSTO 增益集部署至使用者的電腦上的安全位置。

  如需詳細資訊，請參閱 <<c0> [ 使用 Windows Installer 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。

##  <a name="Bypass"></a> 略過功能區反映
 如果您使用建置解決方案[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]，確保您的使用者已安裝最新版的 Visual Studio 2010 Tools for Office 執行階段，當您部署的解決方案。 較舊版本的執行階段會反映到方案組件，找出功能區自訂項目。 此程序會使得 VSTO 增益集載入的速度更加緩慢。

 或者，您可以防止任何版本的 Visual Studio 2010 Tools for Office runtime 使用反映來識別功能區自訂項目。 若要遵循此策略，覆寫`CreateRibbonExtensibility`方法，並明確傳回功能區物件。 如果您 VSTO 增益集未包含任何功能區自訂項目，傳回`null`方法內。

 下列範例會傳回欄位的值為基礎的功能區物件。

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

##  <a name="Perform"></a> 在個別執行緒中執行耗費資源的作業
 請考慮在不同的執行緒中執行耗時的工作 (例如需長時間執行的工作、資料庫連接或其他類型的網路呼叫)。 如需詳細資訊，請參閱 < [Office 中的執行緒支援](../vsto/threading-support-in-office.md)。

> [!NOTE]
>  所有呼叫 Office 物件模型的程式碼，都必須在主執行緒中執行。

## <a name="see-also"></a>另請參閱

- [視需要載入 VSTO 增益集](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [延遲載入 CLR 中的 Office 增益集](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [使用 Visual Studio 建立 VSTO 增益集適用於 Office](create-vsto-add-ins-for-office-by-using-visual-studio.md)
