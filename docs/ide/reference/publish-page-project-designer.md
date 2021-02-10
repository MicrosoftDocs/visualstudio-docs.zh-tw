---
title: 專案設計工具、發行頁
description: '[專案設計工具] 的 [發行] 頁面是用來設定 ClickOnce 部署的屬性。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32bbd09b087639c362fbb5d6a137241c1aab85af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958319"
---
# <a name="publish-page-project-designer"></a>專案設計工具、發行頁

[專案設計工具]  的 [發行]  頁面，可用以設定 ClickOnce 部署的屬性。

若要存取 [發行]  頁面，請選取方案總管 中的專案節點，然後按一下 [專案]  功能表上的 [屬性] 。 當 [ **專案設計工具** ] 出現時，請按一下 [ **發行** ] 索引標籤。

> [!NOTE]
> 這裡描述的一些 ClickOnce 屬性也可以設定於 [發行精靈] 中 (從 [組建] 功能表或按一下此頁面上的 [發行精靈] 按鈕即可使用)。

## <a name="uielement-list"></a>UIElement 清單

 **發行資料夾位置**

指定應用程式的發行位置。 可以是磁碟機路徑 (`C:\deploy\myapplication`)、檔案共用 (`\\server\myapplication`) 或 FTP 伺服器 (`ftp://ftp.microsoft.com/myapplication`)。 請注意，文字必須出現在 [發行位置]  方塊中才能讓瀏覽 (**...**) 按鈕運作。

 **安裝資料夾 URL**

選擇性。 指定使用者前往以安裝應用程式的網站。 只有在它與 [發行位置] 不同時 (例如，將應用程式發行至預備伺服器時) 才是必要項目。

 **安裝模式和設定**

判斷是從 [發行位置]  直接執行應用程式 (選取 [應用程式只能在線上時使用]  時)，還是將應用程式安裝並新增至 [開始]  功能表以及 [控制台]  中的 [新增或移除程式]  項目 (選取 [應用程式也可以在離線時使用]  時)。

針對 WPF 網頁瀏覽器應用程式，[應用程式也可以在離線時使用] 選項已停用，因為這類應用程式只能在上線時使用。

 **應用程式檔案**

開啟 [應用程式檔案] 對話方塊，以用來指定個別檔案的安裝方式和位置。

 **先決條件**

開啟 [必要條件] 對話方塊，以用來指定將必備元件 (例如 .NET Framework) 和應用程式安裝在一起。

 **更新**

開啟 [應用程式更新] 對話方塊，以用來指定應用程式的更新行為。 選取 [應用程式只能在線上時使用]  時無法使用。

 **選項**

開啟 [發行選項] 對話方塊，以用來指定其他進階發行選項。

 **發行版本**

設定應用程式的發行版本號碼；當版本號碼變更時，會以更新形式發行應用程式。 發行版本的每個部分 (**主要**、**次要**、**組建**、**修訂**) 最大值可以是 65355 (<xref:System.UInt16.MaxValue>)，這是 <xref:System.Version> 允許的最大值。

當您使用 ClickOnce 安裝多個版本的應用程式時，安裝會將舊版應用程式移至您指定之發行位置中名為 Archive 的資料夾。 以這種方式封存先前的版本可將安裝目錄與舊版的資料夾分開。

 **隨著每次發行自動遞增修訂**

選擇性。 選取此選項時 (預設)，每次發行應用程式時，發行版本號碼的 [修訂]  部分都會加一。 這樣會以更新形式發行應用程式。

 **發行精靈**

開啟 [發行精靈]。 完成 [發行精靈] 的效果，與執行 [建置]  功能表上的 [發行]  命令相同。

 **立即發行**

使用目前的設定發行應用程式。 這相當於 [發行精靈] 中的 [完成] 按鈕。

## <a name="see-also"></a>另請參閱

- [發行 ClickOnce 應用程式](../../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈嚮導發行 ClickOnce 應用程式](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [如何：指定 Visual Studio 複製檔案的位置](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [如何：指定終端使用者將安裝的位置](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [如何：指定技術支援的連結](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [如何：指定 ClickOnce 離線或線上安裝模式](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [如何：啟用 CD 安裝的 AutoStart](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [如何：設定 ClickOnce 發行版本](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [如何：自動遞增 ClickOnce 發行版本](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [如何：指定哪些檔案是由 ClickOnce 發行](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [如何：使用 ClickOnce 應用程式安裝必要條件](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [如何：管理 ClickOnce 應用程式的更新](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [如何：變更 ClickOnce 應用程式的發行語言](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [如何：指定 ClickOnce 應用程式的開始功能表名稱](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [如何：指定 ClickOnce 應用程式的發行頁面](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [ClickOnce 安全性和部署](../../deployment/clickonce-security-and-deployment.md)
