---
title: VSTO 外接程式的登錄機碼
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416519"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO 外接程式的登錄機碼
  部署使用 Visual Studio 建立的 VSTO 增益集時，您必須建立一組特定的登錄項目。 這些登錄項目可提供讓 Microsoft Office 應用程式探索及載入 VSTO 增益集的資訊。

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 建置專案時，Visual Studio 會在開發電腦上建立這些登錄項目，讓您輕鬆執行和偵錯 VSTO 增益集。 如果使用 ClickOnce 部署 VSTO 外接程式，登錄機碼將自動在最終使用者電腦上創建。 如果使用 Windows 安裝程式部署 VSTO 外接程式，則必須配置安裝程式有限版專案才能在最終使用者電腦上創建登錄機碼。

 如需如何在 VSTO 增益集載入過程中使用登錄項目的詳細資訊，請參閱 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。

> [!NOTE]
> 在本主題中， *增益集 ID* 一詞代表 VSTO 增益集的唯一識別碼。 根據預設，這個識別碼是 VSTO 增益集組件的名稱。

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>註冊當前使用者的 VSTO 載入項與所有使用者
 VSTO 增益集安裝完成後，可以使用兩種方法註冊：

- 僅適用于當前使用者（也就是說，它僅在安裝 VSTO 外接程式時登錄到電腦的使用者可用）。 在這種情況下，登錄機碼在**HKEY_CURRENT_USER**下創建。

- 對於所有使用者（即，登錄到電腦的任何使用者都可以使用 VSTO 外接程式）。 在這種情況下，登錄機碼在**HKEY_LOCAL_MACHINE**下創建。

  以 Visual Studio 建立的所有 VSTO 增益集都能註冊以供目前的使用者使用。 不過，只有在特定情況下，才能註冊 VSTO 增益集讓所有使用者使用。 這些情況取決於電腦上的 Microsoft Office 版本以及 VSTO 增益集的部署方式。

### <a name="deployment-type"></a>部署類型
 如果您使用 ClickOnce 部署 VSTO 增益集，VSTO 增益集只能註冊供目前使用者使用， 這是因為 ClickOnce 僅支援**在 HKEY_CURRENT_USER**下創建金鑰。 如果希望讓電腦的所有使用者都能使用註冊的 VSTO 增益集，則必須使用 Windows Installer 部署 VSTO 增益集。 有關這些部署類型的詳細資訊，請參閱使用[ClickOnce 部署 Office 解決方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)，並使用[Windows 安裝程式部署 Office 解決方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。

## <a name="registry-entries"></a>登錄項目
 所需的 VSTO 外接程式登錄機碼位於以下登錄機碼下，*其中 Root* **是HKEY_CURRENT_USER**或**HKEY_LOCAL_MACHINE，** 具體取決於安裝是針對當前使用者還是所有使用者。

|辦公室應用程式|組態路徑|
|------------------|------------------|
|Visio|*根*[軟體]\\微軟*Visio*_Addins\\*外接程式 ID*|
|所有其他|*根*[軟體]微軟\\ *_Office Office 應用程式名稱*\\\Addins*外接程式 ID*|

> [!NOTE]
> 如果安裝程式的目標是 64 位 Windows 上的所有使用者，則建議它包括兩個登錄機碼，一個在 HKEY_LOCAL_MACHINE_Software_Microsoft 下，另一個在\\HKEY_LOCAL_MACHINE_軟體**WOW6432Node**_Microsoft 配置單元下。 這是因為使用者可以在電腦上使用 32 位或 64 位版本的 Office。
>
>如果安裝程式的目標是當前使用者，則無需安裝到 WOW6432Node，因為HKEY_CURRENT_USER\軟體路徑是共用的。
>
>有關詳細資訊，請參閱[註冊表中的 32 位和 64 位應用程式資料](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 下表列出此登錄機碼下的項目。

|項目|類型|值|
|-----------|----------|-----------|
|**描述**|REG_SZ|必要。 VSTO 增益集的簡短描述。<br /><br /> 當使用者在 Microsoft Office 應用程式之 [選項] **** 對話方塊的 [增益集] **** 窗格中選取 VSTO 增益集時，即會顯示這個描述。|
|**易記名稱**|REG_SZ|必要。 這是 Microsoft Office 應用程式的 [COM 增益集] **** 對話方塊中，所顯示之 VSTO 增益集的描述性名稱。 預設值為 VSTO 增益集 ID。|
|**LoadBehavior**|REG_DWORD|必要。 可指定應用程式何時嘗試載入 VSTO 增益集和 VSTO 增益集目前狀態 (載入或卸載) 的值。<br /><br /> 這個項目預設會設定為 3，指定在啟動時載入 VSTO 增益集。 有關詳細資訊，請參閱[Load行為值](#LoadBehavior)。 **注：** 如果使用者禁用 VSTO 外接程式，則該操作將修改**HKEY_CURRENT_USER**註冊表配置單元中的**LoadAction**值。 對於每個使用者，HKEY_CURRENT_USER配置單元中的**LoadBehavior**值將覆蓋**HKEY_LOCAL_MACHINE**配置單元中定義的預設**LoadBehavior。**|
|**清單**|REG_SZ|必要。 VSTO 增益集部署資訊清單的完整路徑。 路徑可以是本機電腦上的位置、網路共用 (UNC) 或 Web 伺服器 (HTTP)。<br /><br /> 如果使用 Windows Installer 來部署解決方案，您必須在 **資訊清單** 路徑前加上前置詞 **file:///** 。 還必須將&#124;**vstolocal（** 即管道字元 **&#124;** 後跟**vstolocal）** 的字串追加到此路徑的末尾。 如此可以確保解決方案是從安裝資料夾載入，而不是從 ClickOnce 快取載入。 有關詳細資訊，請參閱使用[Windows 安裝程式部署 Office 解決方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。 **注：** 在開發電腦上構建 VSTO 外接程式時，Visual Studio 會自動將 **&#124;vstolocal**字串追加到此登錄機碼中。|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Outlook 表單區域的登錄機碼
 如果您在 Outlook 的 VSTO 增益集中建立自訂表單區域，則必須使用額外的登錄項目向 Outlook 註冊這個表單區域。 系統會在表單區域所支援之各個訊息類別的不同登錄機碼下建立這些項目。 這些登錄機碼位於以下位置，*根*位於**HKEY_CURRENT_USER**或**HKEY_LOCAL_MACHINE。**

 *根*[軟體]微軟\Office\Outlook\Form\\區域*消息類*

 當您建置專案時，Visual Studio 會在開發電腦上建立表單區域登錄項目，如同所有 VSTO 增益集共用的其他登錄項目一樣。 如果使用 ClickOnce 部署 VSTO 外接程式，登錄機碼將自動在最終使用者電腦上創建。 如果使用 Windows 安裝程式部署 VSTO 外接程式，則必須配置安裝程式有限版專案才能在最終使用者電腦上創建登錄機碼。

 有關表單區域登錄機碼的詳細資訊，請參閱[在自訂表單中指定表單區域的位置](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form)。 有關 Outlook 表單區域的詳細資訊，請參閱[創建 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a>載入行為值
 *Root*_Software_Microsoft_Office\\*應用程式名稱*"載入\\項 *"* 下的**LoadBehavior**條目包含指定 VSTO 外接程式的運行時行為的值的位形組合。 最低順序位元 (值 0 和 1) 表示 VSTO 增益集目前處於卸載或載入狀態。 其他位元則表示應用程式嘗試載入 VSTO 增益集的時間。

 通常，當在最終使用者電腦上安裝 VSTO 外接程式時 **，LoadBehavior**條目旨在設置為 0、3 或 16（十進位）。 根據預設，當您建置或發行 VSTO 增益集時，Visual Studio 會將 VSTO 增益集的 **LoadBehavior** 項目設定為 3。

 下表列出 **LoadBehavior** 項目所有可能的值： 這個表格中的部分描述是指手動或以程式設計方式載入 VSTO 增益集。 若要手動載入 VSTO 增益集，請在應用程式的 [COM 增益集] **** 對話方塊中，選取 [VSTO 增益集] 旁的核取方塊。 若要以程式設計方式載入 VSTO 增益集，請將代表 VSTO 增益集之 <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> 物件的 <xref:Microsoft.Office.Core.COMAddIn> 屬性設定為 **true**。

|值 (十進位)|VSTO 增益集狀態|VSTO 增益集載入行為|描述|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|已卸載|不自動載入|應用程式永遠不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 如果成功載入 VSTO 增益集， **LoadBehavior** 值會維持為 0，但 [COM 增益集] **** 對話方塊中的 VSTO 增益集狀態會更新，表示已載入 VSTO 增益集。|
|1|已載入|不自動載入|應用程式永遠不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 儘管**COM 外接程式**對話方塊指示在應用程式啟動後載入 VSTO 外接程式，但在手動或以程式設計方式載入之前不會載入 VSTO 外接程式。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會變成 0，並在應用程式關閉後維持為 0。|
|2|已卸載|啟動時載入|應用程式不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會變成 3，並在應用程式關閉後維持為 3。|
|3|已載入|啟動時載入|應用程式在啟動時嘗試載入 VSTO 增益集。 如果您在 Visual Studio 中建置或發行 VSTO 增益集，這就是預設值。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會維持為 3。 如果載入 VSTO 增益集時發生錯誤， **LoadBehavior** 值會變成 2，並在應用程式關閉後維持為 2。|
|8|已卸載|視需要載入|應用程式不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會變成 9。|
|9|已載入|視需要載入|只有在需要時，應用程式才會載入 VSTO 增益集，例如使用者按下使用 VSTO 增益集功能的 UI 項目時 (例如功能區的自訂按鈕)。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會維持為 9，但 [COM 增益集] **** 對話方塊中的 VSTO 增益集狀態會更新，表示目前已載入 VSTO 增益集。 如果載入 VSTO 增益集時發生錯誤， **LoadBehavior** 值會變成 8。|
|16|已載入|第一次載入，之後則視需求載入|如果您希望依需求載入 VSTO 增益集，請設定為這個值。 使用者首次執行應用程式時，應用程式會載入 VSTO 增益集。 使用者下次執行應用程式時，應用程式會載入 VSTO 增益集已定義的任何 UI 項目，但在使用者按下與 VSTO 增益集相關聯的 UI 項目之前，不會載入 VSTO 增益集。<br /><br /> 應用程式首次成功載入 VSTO 增益集時， **LoadBehavior** 值會在 VSTO 增益集載入時維持為 16。 應用程式關閉後， **LoadBehavior** 值會變成 9。|

## <a name="see-also"></a>另請參閱
- [視覺化工作室中的 Office 解決方案架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [構建 Office 解決方案](../vsto/building-office-solutions.md)
- [部署 Office 解決方案](../vsto/deploying-an-office-solution.md)
 