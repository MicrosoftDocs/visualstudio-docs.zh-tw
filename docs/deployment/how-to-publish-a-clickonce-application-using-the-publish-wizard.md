---
title: 使用發佈嚮導發行 ClickOnce 應用程式
description: 瞭解如何使用 [發佈嚮導] 將 ClickOnce 應用程式提供給使用者使用，包括要使用的發行屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7591513bc52807b87e9df2f0fb65364d5aff2db8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900537"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>如何：使用發佈精靈發佈 ClickOnce 應用程式
若要讓使用者可以使用 ClickOnce 應用程式，您必須將它發行至檔案共用或路徑、FTP 伺服器或卸除式媒體。 您可以使用 [發佈精靈] 發佈應用程式；[專案設計工具] 的 [發佈] 頁面上也有提供與發佈相關的其他屬性。 如需詳細資訊，請參閱[發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)。

在執行 [發行精靈] 之前，您應該適當設定發行屬性。 例如，如果您要指定用於簽署 ClickOnce 應用程式的金鑰，您可以在 [專案設計工具] 的 [簽署] 頁面上執行這項操作。 如需詳細資訊，請參閱 [安全的 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。

> [!NOTE]
> 當您使用 ClickOnce 安裝多個版本的應用程式時，安裝會將繼承應用程式移至您指定的發佈位置 *中名為*[封存] 的資料夾。 以這種方式封存先前的版本可將安裝目錄與舊版的資料夾分開。

> [!NOTE]
> 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="to-publish-to-a-file-share-or-path"></a>發行至檔案共用或路徑

1. 在 [方案總管] 中，選取應用程式專案。

2. 在 [**組建**] 功能表上，按一下 [**發行***專案名稱*]。

    [發行精靈] 隨即出現。

3. 在 [您要將應用程式發佈至何處?] 頁面上，請使用其中一種顯示的格式，輸入有效 FTP 伺服器位址或有效檔案路徑，然後按一下 [下一步]。

4. 在 [使用者將如何安裝應用程式?] 頁面上，選取使用者將安裝應用程式的位置：

   - 如果使用者將從網站安裝，請按一下 [從網站]，然後輸入對應至上一個步驟中輸入之檔案路徑的 URL。 按一下 [下一步] 。 (當您指定 FTP 位址做為發行位置時，通常會使用這個選項。 不支援直接從 FTP 下載。 因此，您必須在此輸入 URL。)

   - 如果使用者將從檔案共用直接安裝應用程式，請按一下 [從 UNC 路徑或檔案共用]，然後按一下 [下一步]。 (這是用來發佈 *c:\deploy\myapp* 或 *\\\\server\myapp* 格式的位置。)

   - 如果使用者將從抽取式媒體安裝，請按一下 [從 CD-ROM 或 DVD-ROM]，然後按一下 [下一步]。

5. 在 [是否可以在離線時使用應用程式?] 頁面上，按一下適當的選項：

   - 如果您要讓使用者在中斷網路連線時可以執行應用程式，請按一下 [是，這個應用程式可於線上或離線時使用]。 [開始] 功能表上將會建立這個應用程式的捷徑。

   - 如果您要從發佈位置直接執行應用程式，請按一下 [否，這個應用程式只能在線上時使用]。 [開始] 功能表上將不會建立捷徑。

     選取 [下一步] 以繼續操作。

6. 按一下 [完成] 發佈應用程式。

    發行狀態會隨即顯示在狀態通知區域中。

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>發行至 CD-ROM 或 DVD-ROM

1. 在 [方案總管] 中，以滑鼠右鍵按一下應用程式專案，然後按一下 [屬性]。

    [ **專案設計** 工具] 隨即出現。

2. 按一下 [發佈] 索引標籤，開啟 [專案設計工具] 中的 [發佈] 頁面，然後按一下 [發佈精靈] 按鈕。

    [發行精靈] 隨即出現。

3. 在 [您要將應用程式發佈至何處?] 頁面上，輸入將要發佈應用程式的檔案路徑或 FTP 位置，例如 *d:\deploy*。 然後按 [下一步] 以繼續作業。

4. 在 [使用者要如何安裝應用程式?] 頁面上，按一下 [從 CD-ROM 或 DVD-ROM]，然後按一下 [下一步]。

   > [!NOTE]
   > 如果您要在 CD-ROM 插入光碟機時即自動執行安裝，請在 [專案設計工具] 中開啟 [發佈] 頁面，並按一下 [選項] 按鈕，然後在 [發佈選項精靈] 中，選取 [若是使用光碟安裝，在插入光碟後自動啟動安裝程式]。

5. 如果您使用 CD-ROM 散發應用程式，可能會想要從網站提供更新。 在 [應用程式會在哪裡檢查更新檔?] 頁面中，選擇更新選項：

   - 如果應用程式會檢查更新檔，請按一下 [應用程式會從下列位置檢查更新檔]，然後輸入要張貼更新的位置。 這可以是檔案位置、網站或 FTP 伺服器。

   - 如果應用程式不會檢查更新檔，請按一下 [應用程式將不會檢查更新檔]。

     選取 [下一步] 以繼續操作。

6. 按一下 [完成] 發佈應用程式。

    發行狀態會隨即顯示在狀態通知區域中。

   > [!NOTE]
   > 在發行完成後，您必須使用 CD 燒錄機或 DVD 燒錄機，將檔案從步驟 3 中指定的位置複製到 CD-ROM 或 DVD-ROM 媒體。

## <a name="see-also"></a>另請參閱

- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)