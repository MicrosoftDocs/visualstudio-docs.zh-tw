---
title: 發佈頁面、專案設計工具 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 391e6c457dd09afa154c46cbc8644f028052cb32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665698"
---
# <a name="publish-page-project-designer"></a>專案設計工具、發行頁
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[專案設計工具] **** 的 [發行] **** 頁面，可用以設定 ClickOnce 部署的屬性。

 若要存取 [發行] **** 頁面，請選取方案總管 **** 中的專案節點，然後按一下 [專案] **** 功能表上的 [屬性] ****。 當 [ **專案設計工具** ] 出現時，請按一下 [ **發行** ] 索引標籤。

> [!NOTE]
> 這裡描述的一些 ClickOnce 屬性也可以設定於 [發行精靈]**** 中 (從 [組建]**** 功能表或按一下此頁面上的 [發行精靈]**** 按鈕即可使用)。

## <a name="uielement-list"></a>UIElement 清單
 **發行資料夾位置** 指定應用程式的發行位置。 可以是磁碟機路徑 (`C:\deploy\myapplication`)、檔案共用 (`\\server\myapplication`)、FTP 伺服器 (`ftp://ftp.microsoft.com/myapplication`) 或網站 (`http://www.microsoft.com/myapplication`)。 請注意，文字必須出現在 [發行位置] **** 方塊中才能讓瀏覽 (**...**) 按鈕運作。

 根據預設，如果您已安裝 IIS，發行位置為 `http://localhost/<projectname>/` ；如果未安裝 IIS，則為 `publish\` 目錄。 如果您的電腦執行 Windows Vista，則不論是否安裝 IIS，預設值一律都會是 `publish\` 目錄。

 **安裝資料夾 URL** 選。 指定使用者前往以安裝應用程式的網站。 只有在它與 [發行位置] **** 不同時 (例如，將應用程式發行至預備伺服器時) 才是必要項目。

 **安裝模式和設定**判斷應用程式是否直接從**發佈位置**執行 (當**應用程式只能在線上使用**時) 或已安裝並新增至 [**開始**] 功能表，以及當**應用程式離線**時，**主控台** (中的 [**新增或移除程式**] 專案，) 選取。

 針對 WPF Web 瀏覽器應用程式，停用 [應用程式也可以在離線時使用] **** 選項，因為這類應用程式只能在上線時使用。

 **應用程式檔** 開啟 [ [應用程式檔] 對話方塊](https://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8)，用來指定個別檔案的安裝方式和位置。

 **必要條件** 開啟 [ [必要條件] 對話方塊](../../ide/reference/prerequisites-dialog-box.md)，用來指定要與應用程式一起安裝的先決條件元件，例如 .NET Framework。

 **更新** 開啟 [ [應用程式更新] 對話方塊](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)，用來指定應用程式的更新行為。 選取 [應用程式只能在線上時使用] **** 時無法使用。

 **選項** 開啟 [ [發行選項] 對話方塊](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)，用來指定其他 advanced 發行選項。

 **發佈版本** 設定應用程式的發行版本號碼;當版本號碼變更時，就會將應用程式發佈為更新。 發行版本的每個部分 (**主要**、**次要**、**組建**、**修訂**) 最大值可以是 65355 (<xref:System.UInt16.MaxValue>)，這是 <xref:System.Version> 允許的最大值。

 當您使用 ClickOnce 安裝多個版本的應用程式時，安裝會將舊版應用程式移至您指定之發行位置中名為 Archive 的資料夾。 以這種方式封存先前的版本可將安裝目錄與舊版的資料夾分開。

 **每次發行時自動遞增修訂** 選。 選取此選項時 (預設)，每次發行應用程式時，發行版本號碼的 [修訂] **** 部分都會加一。 這樣會以更新形式發行應用程式。

 **發佈嚮導** 開啟 [ [發佈嚮導]](https://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872)。 完成 [發行精靈] 的效果，與執行 [建置] **** 功能表上的 [發行] **** 命令相同。

 **立即發佈** 使用目前的設定發佈應用程式。 這相當於 [發行精靈]**** 中的 [完成]**** 按鈕。

## <a name="see-also"></a>另請參閱
 [發行 Clickonce 應用程式](../../deployment/publishing-clickonce-applications.md)[如何：使用發佈嚮導發行 clickonce 應用程式](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)[如何：指定 Visual Studio 複製](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)檔案的位置[如何](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)：指定[技術支援的連結](../../deployment/how-to-specify-a-link-for-technical-support.md)如何：指定[ClickOnce 離線或線上安裝模式如何：指定 CLICKONCE 離線或線上安裝模式](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)[如何：啟用自動啟動 CD 安裝](../../deployment/how-to-enable-autostart-for-cd-installations.md)[如何：設定 clickonce 發行版本](../../deployment/how-to-set-the-clickonce-publish-version.md)[如何：自動遞增 Clickonce 發行版本](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)[如何：指定 Clickonce 發行](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)的[檔案如何：](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [管理 Clickonce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)應用程式的更新如何：指定 Clickonce 應用程式的[發行語言](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)如何：指定 Clickonce 應用程式的[開始功能表名稱如何：指定 clickonce 應用程式的開始功能表名稱如何：指定 clickonce 應用程式的開始功能表名稱](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)如何[：指定 ClickOnce 應用程式的發行頁面](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md) [clickonce 安全性和部署](../../deployment/clickonce-security-and-deployment.md)
