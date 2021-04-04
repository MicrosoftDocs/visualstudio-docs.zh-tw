---
title: 建立 ClickOnce 應用程式的自訂安裝程式
description: 瞭解自訂安裝程式如何以無訊息模式安裝和更新以 .exe 檔案為基礎的 ClickOnce 應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7ae131026a94fa368d55bad1d8cd2164b6f960b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216926"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>逐步解說：為 ClickOnce 應用程式建立自訂安裝程式
任何以 *.exe* 檔案為基礎的 ClickOnce 應用程式，都可以透過自訂安裝程式以無訊息方式安裝和更新。 自訂安裝程式可以在安裝期間執行自訂的使用者體驗，包括安全性和維護作業的自訂對話方塊。 若要執行安裝作業，自訂安裝程式會使用 <xref:System.Deployment.Application.InPlaceHostingManager> 類別。 本逐步解說示範如何建立以無訊息方式安裝 ClickOnce 應用程式的自訂安裝程式。

## <a name="prerequisites"></a>必要條件

### <a name="to-create-a-custom-clickonce-application-installer"></a>若要建立自訂 ClickOnce 應用程式安裝程式

1. 在 ClickOnce 應用程式中，新增對 Deployment 和 System.object 的參考。

2. 將新類別新增至您的應用程式，並指定任何名稱。 這個逐步解說使用的名稱為 `MyInstaller`。

3. 將下列或指示詞新增 `Imports` `using` 至新類別的頂端。

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. 將下列方法新增至您的類別。

     這些方法會呼叫 <xref:System.Deployment.Application.InPlaceHostingManager> 方法來下載部署資訊清單、判斷提示適當的許可權、要求使用者安裝許可權，然後將應用程式下載並安裝到 ClickOnce 快取中。 自訂安裝程式可以指定 ClickOnce 應用程式是預先信任的，也可以將信任決策延後至 <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> 方法呼叫。 此程式碼會預先信任應用程式。

    > [!NOTE]
    > 預先信任所指派的許可權不能超過自訂安裝程式程式碼的許可權。

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs" id="Snippet1":::

5. 若要從您的程式碼嘗試安裝，請呼叫 `InstallApplication` 方法。 例如，如果您將類別命名為 `MyInstaller` ，您可能會 `InstallApplication` 以下列方式呼叫。

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>下一步
 ClickOnce 應用程式也可以加入自訂的更新邏輯，包括要在更新程式期間顯示的自訂使用者介面。 如需詳細資訊，請參閱<xref:System.Deployment.Application.UpdateCheckInfo>。 ClickOnce 應用程式也可以使用元素來隱藏標準 [開始] 功能表專案、快捷方式，以及新增或移除程式專案 `<customUX>` 。 如需詳細資訊，請參閱[ \<entryPoint> element](../deployment/entrypoint-element-clickonce-application.md)和 <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> 。

## <a name="see-also"></a>另請參閱
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
- [\<entryPoint> 元素](../deployment/entrypoint-element-clickonce-application.md)
