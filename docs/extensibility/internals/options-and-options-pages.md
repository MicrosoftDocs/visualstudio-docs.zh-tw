---
title: 選項與選項頁面 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706830"
---
# <a name="options-and-options-pages"></a>選項和選項頁
按下「**工具**」選單上**的選項**將開啟「**選項」** 對話框。 此對話框中的選項統稱為選項頁。 導航窗格中的樹控件包括選項類別,每個類別都有選項頁。 選擇頁面時,其選項將顯示在右側窗格中。 這些頁面允許您更改確定 VSPackage 狀態的選項的值。

## <a name="support-for-options-pages"></a>支援選項頁
 該<xref:Microsoft.VisualStudio.Shell.Package>類支援創建選項頁和選項類別。 類<xref:Microsoft.VisualStudio.Shell.DialogPage>實現一個選項頁。

 的<xref:Microsoft.VisualStudio.Shell.DialogPage>默認實現向屬性的通用網格中的使用者提供其公共屬性。 您可以通過重寫頁面上的各種方法來自定義此行為,以建立具有其自己的使用者介面 (UI) 的自定義選項頁。 關於詳細資訊,請參閱[建立選項頁](../../extensibility/creating-an-options-page.md)。

 類<xref:Microsoft.VisualStudio.Shell.DialogPage><xref:Microsoft.VisualStudio.Shell.IProfileManager>實現 ,它為選項頁和用戶設置提供持久性。 如果屬性可以轉換為字串並從<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>字串<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>轉換,則和方法的預設實現將屬性保留為註冊表的使用者部分。

## <a name="options-page-registry-path"></a>選項頁面註冊表路徑
 默認情況下,由選項頁管理的屬性的註冊錶路徑通過組合<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>、單詞DialogPage和選項頁類的類型名稱來確定。 例如,選項頁類的定義可能如下。

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 如果<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>是 HKEY_CURRENT_USER\軟體\Microsoft_VisualStudio_8.0Exp,則屬性名稱和值對是HKEY_CURRENT_USER\軟體\微軟_VisualStudio_8.0Exp_DialogPage_公司.OptionsPage.OptionsPage。"選項頁"

 選項頁的註冊表路徑通過組合<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>(word、ToolsOptionsPages 和選項頁類別和名稱)來確定。 例如,如果"自定義選項頁"具有類別"我的選項頁",並且<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>是HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_8.0Exp,則選項頁具有註冊表項,HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_8.0Exp_ToolsOptionPages_我的選項頁面\自定義。

## <a name="toolsoptions-page-attributes-and-layout"></a>工具/選項頁面屬性和佈局
 該<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性確定自定義選項頁分組到 **「選項」** 對話框的導航樹中的類別。 該<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性將選項頁與提供介面的 VSPackage 關聯。 請考慮下列程式碼片段：

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 這將聲明「我的包」提供兩個選項頁面:選項頁常規和選項頁面自定義。 在「**選項」** 對話框中,兩個選項頁分別顯示在「**我的選項頁」** 類別中,分別顯示為 **「一般****」 和「自訂**」 。

## <a name="option-attributes-and-layout"></a>選項屬性與佈局
 頁面提供的使用者介面 (UI) 確定自定義選項頁中選項的外觀。 泛型選項頁中選項的佈局、標記和說明由以下屬性確定:

- <xref:System.ComponentModel.CategoryAttribute>確定選項的類別。

- <xref:System.ComponentModel.DisplayNameAttribute>確定選項的顯示名稱。

- <xref:System.ComponentModel.DescriptionAttribute>確定選項的說明。

  > [!NOTE]
  > 等效屬性、SR 類別、LocDisplayName 和 SR描述使用字串資源進行當地語系化,並在[託管專案範例中](/azure/devops/integrate/index)定義。

  請考慮下列程式碼片段：

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  選項整數選項在「**我的選項**」類別中顯示為**整數選項**。 如果選擇了該選項,則說明「**我的整數」選項**將顯示在描述框中。

## <a name="accessing-options-pages-from-another-vspackage"></a>從其他 VS 套件存取選項頁
 可以使用自動化模型從另一個 VSPackage 以程式設計方式存取承載和管理選項頁的 VSPackage。 例如,在以下代碼中,VSPackage 註冊為託管選項頁。

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 以下片段從 MyOptionPage 取得 OptionInteger 的值:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 當<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>屬性註冊選項頁時,如果屬性`SupportsAutomation`的`true`參數為 ,則該頁將註冊在自動化屬性鍵下。 自動化檢查此註冊表項以查找關聯的 VSPackage,然後自動化透過託管選項頁(本例中為"我的網格頁")訪問該屬性。

 自動化屬性的註冊錶路徑通過組合<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>、單詞、自動化屬性和選項頁類別和名稱來確定。 例如,如果選項頁具有"我的類別"類別、"我的網格頁"名稱以及<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>、HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_8.0Exp,則自動化屬性具有註冊表項HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_8.0Exp_自動化屬性\我的類別\我的網格頁面。

> [!NOTE]
> 規範名稱"我的Category.My網格頁"是此鍵的名稱子鍵的值。
