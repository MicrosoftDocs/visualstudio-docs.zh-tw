---
title: 確認 IIS 屬性設定 |Microsoft Docs
description: 瞭解如何使用 IIS 管理工具來確認您為 web 應用程式設定的 IIS 屬性設定。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b627fbd3d4875699faa28f551d68f5a99bd63340
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150544"
---
# <a name="how-to-verify-iis-property-settings"></a>如何：檢查 IIS 屬性設定

您可以使用 IIS 系統管理工具設定 Web 應用程式的屬性。 必須正確設定這些屬性才能順利執行應用程式，因此驗證這些設定通常都是疑難排解的必要步驟。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="to-check-iis-settings-for-the-web-application"></a>若要檢查 Web 應用程式的 IIS 設定

1. 開啟 [系統管理工具] 視窗：在 [開始] 功能表上，指向 [程式集]，然後按一下 [系統管理工具]。 如果 [程式集] 功能表中並未顯示 [系統管理工具]，請從 [控制台] 中尋找這個功能。

   - 在 Windows 2000 中，請選取 [網際網路服務管理員]。

   - 在 Windows XP 中，請選取 [網際網路資訊服務]。

   - 在 Windows Server 2003 中，請按兩下 [管理您的伺服器]。

        [管理您的伺服器] 視窗隨即開啟。 在 [應用程式伺服器] 中，按一下 [管理此應用程式伺服器]。

        [應用程式伺服器] 視窗隨即開啟。 在左窗格中開啟 [網際網路資訊服務 (IIS) 管理員] 節點。

2. 在對話方塊中，按一下電腦的樹狀目錄控制項節點。 按一下 [網站] 節點，然後選取 Web 應用程式的節點。 這將會是 [網站] 節點，因此跟 [預設網站] 節點同層級，或是在現有網站節點之下的虛擬目錄節點。

3. 以滑鼠右鍵按一下 Web 應用程式，並在捷徑功能表上按一下 [屬性]。

4. 驗證 Web 應用程式的安全性設定：

   1. 在 Web 應用程式的 [屬性] 視窗中，按一下 [目錄安全性] 索引標籤，然後按一下 [編輯]。

   2. 在 [驗證方法] 對話方塊中，選取 [啟用匿名存取] 和 [整合式 Windows 驗證] (如果尚未選取)。

   3. 按一下 [確定] 關閉 [驗證方法] 對話方塊。

5. 對於 ATL Server 應用程式，請驗證偵錯動詞命令 (DEBUG Verb) 是否與您的 ISAPI 副檔名有關聯。 如需詳細資訊，請參閱 how [to：使 DEBUG 動詞與 Extension 產生關聯](/previous-versions/ms165022(v=vs.100))。

6. 針對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式，請確定應用程式的虛擬資料夾在 [網際網路資訊服務 (IIS) 管理員]、[網際網路服務管理員] 或 [網際網路資訊服務] 中已設定 [應用程式名稱]。

   1. 在 Web 應用程式的 [屬性] 視窗中，選取 [目錄] 索引標籤 (如果應用程式在虛擬目錄中) 或是 [主目錄] 索引標籤 (如果應用程式在網站中)。

   2. 驗證 [本機路徑] 中的名稱，是否符合實際部署應用程式的目錄名稱。

   3. 在 [應用程式設定] 下方，鍵入包含應用程式的根目錄名稱。

   4. 按一下 [確定] 以關閉 [內容] 對話方塊。

7. 針對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式，按一下 [ASP.NET] 索引標籤，並且驗證是否已指定正確的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 版本。

8. 按一下 [確定] 以關閉 [內容] 對話方塊。

9. 按一下 [確定] 以關閉 [網際網路資訊服務 (IIS) 管理員]、[網際網路服務管理員] 或 [網際網路資訊服務] 對話方塊。

## <a name="see-also"></a>另請參閱

- [疑難排解](../debugger/debugging-web-applications-troubleshooting.md)