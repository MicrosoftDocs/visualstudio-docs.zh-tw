---
title: VSTO 增益集的登錄專案
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
ms.openlocfilehash: 464820258e5c20474d74f92eb108344deccc49f1
ms.sourcegitcommit: 0a8855572c6c88f4b2ece232c04aa124fbd9cec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955045"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO 增益集的登錄專案
  部署使用 Visual Studio 建立的 VSTO 增益集時，您必須建立一組特定的登錄項目。 這些登錄項目可提供讓 Microsoft Office 應用程式探索及載入 VSTO 增益集的資訊。

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 建置專案時，Visual Studio 會在開發電腦上建立這些登錄項目，讓您輕鬆執行和偵錯 VSTO 增益集。 如果您使用 ClickOnce 部署 VSTO 增益集，登錄專案會自動建立在使用者電腦上。 如果您使用 Windows Installer 部署 VSTO 增益集，您必須設定 InstallShield 限量版專案來建立使用者電腦上的登錄專案。

 如需如何在 VSTO 增益集載入過程中使用登錄項目的詳細資訊，請參閱 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。

> [!NOTE]
> 在本主題中， *增益集 ID* 一詞代表 VSTO 增益集的唯一識別碼。 根據預設，這個識別碼是 VSTO 增益集組件的名稱。

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>為目前使用者和所有使用者註冊 VSTO 增益集
 VSTO 增益集安裝完成後，可以使用兩種方法註冊：

- 僅限目前使用者（亦即，只有在安裝 VSTO 增益集時，登入電腦的使用者才能使用）。 在此情況下，登錄專案會建立在**HKEY_CURRENT_USER**之下。

- 針對所有使用者（也就是登入電腦的任何使用者都可以使用 VSTO 增益集）。 在此情況下，登錄專案會建立在**HKEY_LOCAL_MACHINE**之下。

  以 Visual Studio 建立的所有 VSTO 增益集都能註冊以供目前的使用者使用。 不過，只有在特定情況下，才能註冊 VSTO 增益集讓所有使用者使用。 這些情況取決於電腦上的 Microsoft Office 版本以及 VSTO 增益集的部署方式。

### <a name="deployment-type"></a>部署類型
 如果您使用 ClickOnce 部署 VSTO 增益集，VSTO 增益集只能註冊供目前使用者使用， 這是因為 ClickOnce 僅支援在**HKEY_CURRENT_USER**下建立索引鍵。 如果希望讓電腦的所有使用者都能使用註冊的 VSTO 增益集，則必須使用 Windows Installer 部署 VSTO 增益集。 如需這些部署類型的詳細資訊，請參閱[使用 ClickOnce 部署 office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)和[使用 Windows Installer 部署 office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。

## <a name="registry-entries"></a>登錄項目
 必要的 VSTO 增益集登錄專案位於下列登錄機碼底下，其中*根* **HKEY_CURRENT_USER**或**HKEY_LOCAL_MACHINE**取決於目前使用者或所有使用者的安裝。

|Office 應用程式|組態路徑|
|------------------|------------------|
|Visio|*Root*\Software\Microsoft\\*Visio*\ADDINS\\*增益集識別碼*|
|所有其他|*根*\Software\Microsoft\Office\\*Office 應用程式名稱*\ADDINS\\*增益集識別碼*|

> [!NOTE]
> 如果安裝程式是以64位 Windows 上的所有使用者為目標，建議包含兩個登錄專案，一個在 HKEY_LOCAL_MACHINE \Software\Microsoft 底下，另一個位於 HKEY_LOCAL_MACHINE \Software\\**WOW6432Node**\Microsoft hive 底下。 這是因為使用者可以在電腦上使用32位或64位版本的 Office。
>
>如果安裝程式是以目前的使用者為目標，則不需要將它安裝到 WOW6432Node，因為 HKEY_CURRENT_USER 的 \Software 路徑是共用的。
>
>如需詳細資訊，請參閱[Registry 中的32位和64位應用程式資料](https://docs.microsoft.com/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 下表列出此登錄機碼下的項目。

|進入|類型|{2&gt;值&lt;2}|
|-----------|----------|-----------|
|**說明**|REG_SZ|必要項。 VSTO 增益集的簡短描述。<br /><br /> 當使用者在 Microsoft Office 應用程式之 [選項] 對話方塊的 [增益集] 窗格中選取 VSTO 增益集時，即會顯示這個描述。|
|**FriendlyName**|REG_SZ|必要項。 這是 Microsoft Office 應用程式的 [COM 增益集] 對話方塊中，所顯示之 VSTO 增益集的描述性名稱。 預設值為 VSTO 增益集 ID。|
|**LoadBehavior**|REG_DWORD|必要項。 可指定應用程式何時嘗試載入 VSTO 增益集和 VSTO 增益集目前狀態 (載入或卸載) 的值。<br /><br /> 這個項目預設會設定為 3，指定在啟動時載入 VSTO 增益集。 如需詳細資訊，請參閱[LoadBehavior values](#LoadBehavior)。 **注意：** 如果使用者停用 VSTO 增益集，該動作會修改**HKEY_CURRENT_USER**登錄 hive 中的**LoadBehavior**值。 針對每個使用者，HKEY_CURRENT_USER hive 中**LoadBehavior**值的值會覆寫**HKEY_LOCAL_MACHINE** hive 中定義的預設**LoadBehavior** 。|
|**Manifest**|REG_SZ|必要項。 VSTO 增益集部署資訊清單的完整路徑。 路徑可以是本機電腦上的位置、網路共用 (UNC) 或 Web 伺服器 (HTTP)。<br /><br /> 如果使用 Windows Installer 來部署解決方案，您必須在 **資訊清單** 路徑前加上前置詞 **file:///** 。 您也必須將字串 **&#124;vstolocal** （也就是後面接著**vstolocal**的 **&#124;** 管道字元）附加到此路徑的結尾。 如此可以確保解決方案是從安裝資料夾載入，而不是從 ClickOnce 快取載入。 如需詳細資訊，請參閱[使用 Windows Installer 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。 **注意：** 當您在開發電腦上建立 VSTO 增益集時，Visual Studio 會自動將 **&#124;vstolocal**字串附加至這個登錄專案。|

### <a name="OutlookEntries"></a>Outlook 表單區域的登錄專案
 如果您在 Outlook 的 VSTO 增益集中建立自訂表單區域，則必須使用額外的登錄項目向 Outlook 註冊這個表單區域。 系統會在表單區域所支援之各個訊息類別的不同登錄機碼下建立這些項目。 這些登錄機碼位於下列位置，其中*Root*是**HKEY_CURRENT_USER**或**HKEY_LOCAL_MACHINE**。

 *根*\Software\Microsoft\Office\Outlook\FormRegions\\*message 類別*

 當您建置專案時，Visual Studio 會在開發電腦上建立表單區域登錄項目，如同所有 VSTO 增益集共用的其他登錄項目一樣。 如果您使用 ClickOnce 部署 VSTO 增益集，登錄專案會自動建立在使用者電腦上。 如果您使用 Windows Installer 部署 VSTO 增益集，您必須設定 InstallShield 限量版專案來建立使用者電腦上的登錄專案。

 如需表單區域登錄專案的詳細資訊，請參閱[在自訂表單中指定表單區域的位置](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form)。 如需 Outlook 表單區域的詳細資訊，請參閱[建立 outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

## <a name="LoadBehavior"></a>LoadBehavior 值
 *根*\Software\Microsoft\Office\\*應用程式名稱* *\\\Addins*下的**LoadBehavior**專案會包含值的位元組合，這些值會指定 VSTO 增益集的執行時間行為。 最低順序位元 (值 0 和 1) 表示 VSTO 增益集目前處於卸載或載入狀態。 其他位元則表示應用程式嘗試載入 VSTO 增益集的時間。

 一般來說，當 VSTO 增益集安裝在終端使用者電腦上時， **LoadBehavior**專案會設定為0、3或16（十進位）。 根據預設，當您建置或發行 VSTO 增益集時，Visual Studio 會將 VSTO 增益集的 **LoadBehavior** 項目設定為 3。

 下表列出 **LoadBehavior** 項目所有可能的值： 這個表格中的部分描述是指手動或以程式設計方式載入 VSTO 增益集。 若要手動載入 VSTO 增益集，請在應用程式的 [COM 增益集] 對話方塊中，選取 [VSTO 增益集] 旁的核取方塊。 若要以程式設計方式載入 VSTO 增益集，請將代表 VSTO 增益集之 <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> 物件的 <xref:Microsoft.Office.Core.COMAddIn> 屬性設定為 **true**。

|值 (十進位)|VSTO 增益集狀態|VSTO 增益集載入行為|描述|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|已卸載|不自動載入|應用程式永遠不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 如果成功載入 VSTO 增益集， **LoadBehavior** 值會維持為 0，但 [COM 增益集] 對話方塊中的 VSTO 增益集狀態會更新，表示已載入 VSTO 增益集。|
|1|已載入|不自動載入|應用程式永遠不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 雖然 [ **COM 增益集**] 對話方塊指出 vsto 增益集會在應用程式啟動後載入，但在手動或以程式設計方式載入 vsto 增益集之前，不會載入它。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會變成 0，並在應用程式關閉後維持為 0。|
|2|已卸載|啟動時載入|應用程式不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會變成 3，並在應用程式關閉後維持為 3。|
|3|已載入|啟動時載入|應用程式在啟動時嘗試載入 VSTO 增益集。 如果您在 Visual Studio 中建置或發行 VSTO 增益集，這就是預設值。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會維持為 3。 如果載入 VSTO 增益集時發生錯誤， **LoadBehavior** 值會變成 2，並在應用程式關閉後維持為 2。|
|8|已卸載|視需要載入|應用程式不會嘗試自動載入 VSTO 增益集。 使用者可以嘗試手動載入 VSTO 增益集，或是以程式設計方式載入 VSTO 增益集。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會變成 9。|
|9|已載入|視需要載入|只有在需要時，應用程式才會載入 VSTO 增益集，例如使用者按下使用 VSTO 增益集功能的 UI 項目時 (例如功能區的自訂按鈕)。<br /><br /> 如果應用程式成功載入 VSTO 增益集， **LoadBehavior** 值會維持為 9，但 [COM 增益集] 對話方塊中的 VSTO 增益集狀態會更新，表示目前已載入 VSTO 增益集。 如果載入 VSTO 增益集時發生錯誤， **LoadBehavior** 值會變成 8。|
|16|已載入|第一次載入，之後則視需求載入|如果您希望依需求載入 VSTO 增益集，請設定為這個值。 使用者首次執行應用程式時，應用程式會載入 VSTO 增益集。 使用者下次執行應用程式時，應用程式會載入 VSTO 增益集已定義的任何 UI 項目，但在使用者按下與 VSTO 增益集相關聯的 UI 項目之前，不會載入 VSTO 增益集。<br /><br /> 應用程式首次成功載入 VSTO 增益集時， **LoadBehavior** 值會在 VSTO 增益集載入時維持為 16。 應用程式關閉後， **LoadBehavior** 值會變成 9。|

## <a name="see-also"></a>請參閱
- [Visual Studio 中的 Office 方案架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [組建 Office 方案](../vsto/building-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
