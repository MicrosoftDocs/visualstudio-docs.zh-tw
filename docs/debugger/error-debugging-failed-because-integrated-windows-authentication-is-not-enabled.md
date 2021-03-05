---
description: 因為驗證錯誤，所以無法對要求偵錯之使用者進行驗證。
title: 因為未啟用整合式 Windows 驗證，所以無法進行偵錯工具 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a3f95359c7963ca7da3d59f81aa471424c23de8a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147025"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>錯誤：偵錯失敗，因為整合式 Windows 驗證沒有啟用
因為驗證錯誤，所以無法對要求偵錯之使用者進行驗證。 這種情形可能會在您嘗試逐步執行 Web 應用程式或 XML Web Service 時發生。 造成這個錯誤的原因之一是未啟用整合式 Windows 驗證。 若要啟用該驗證，請遵循「若要啟用整合式 Windows 驗證」內所述的步驟進行。

 如果已經啟用整合式 Windows 驗證，但是仍然出現這個錯誤，可能是因為啟用 [Windows 網域伺服器的摘要式驗證]，所以造成這個錯誤。 在此情況下，您應該聯絡網路系統管理員。

### <a name="to-enable-integrated-windows-authentication"></a>若要啟用整合式 Windows 驗證

1. 使用系統管理員帳戶登入 Web 伺服器。

2. 按一下 [ **開始** ]，然後按一下 [ **控制台**]。

3. 在 [控制台] 中按兩下 [系統管理工具]。

4. 按兩下 [Internet Information Services]。

5. 按一下 [Web 伺服器] 節點。

     此時伺服器名稱下方會開啟 [網站] 資料夾。

6. 您可以為所有網站或個別網站設定驗證。 若要為所有網站設定驗證，請以滑鼠右鍵按一下 [網站] 資料夾，然後按一下 [內容]。 若要為個別網站設定驗證，請開啟 [網站] 資料夾，以滑鼠右鍵按一下個別網站，然後按一下 [內容]。

     [內容] 對話方塊隨即出現。

7. 按一下 [目錄安全性] 索引標籤。

8. 在 [匿名存取及驗證控制] 區段中，按一下 [編輯]。

     [驗證方法] 對話方塊隨即出現。

9. 在 [驗證存取] 下，選取 [整合式 Windows 驗證]。

10. 按一下 [確定] 關閉 [驗證方法] 對話方塊。

11. 按一下 [確定] 以關閉 [內容] 對話方塊。

12. 關閉 [Internet Information Services] 視窗。

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>若要在 Windows Vista/IIS 7 內啟用整合式 Windows 驗證

1. 使用系統管理員帳戶登入 Web 伺服器。

2. 如果您先前未開啟 [Windows 驗證] 和 [II6 管理相容性]，請遵循下列步驟來執行此動作：

    1. 按一下 [ **開始**]，按一下 [ **控制台** ]，然後按一下 [ **程式**]。

    2. 按一下 [程式和功能] 下的 [開啟或關閉 Windows 功能]。

         [使用者帳戶控制] 對話方塊隨即出現，並詢問您是否同意繼續進行。

    3. 按一下 [繼續] 。

         [Windows 功能] 對話方塊隨即出現。

    4. 在功能清單中，展開 [Internet Information Services] 節點。

    5. 在 [Internet Information Services] 下，展開 [全球資訊網服務] 節點。

    6. 在 [全球資訊網服務] 下，按一下 [安全性]。

    7. 按一下 [Windows 驗證]。

    8. 在 [Internet Information Services] 下，展開 [Web 管理工具] 節點。

    9. 在 [Web 管理工具] 下，展開 [IIS 6 管理相容性] 節點，並選取 [IIS 6 Metabase 及 IIS 6 設定相容性] 核取方塊。

    10. 在 [Web 管理工具] 下，選取 [IIS 管理主控台]，再按一下 [確定]。

    11. 重新啟動電腦，這些變更就會生效。

3. 按一下 [開始]，然後按一下 [控制台]。

4. 按一下 [傳統檢視]，然後按兩下 [系統管理工具]。

5. 在 [名稱] 一欄中，按兩下 [Internet Information Services (IIS) 管理員]。

6. 在 [連線] 一欄中，展開伺服器的節點。

     此時伺服器名稱下方會開啟 [網站] 資料夾。

7. 展開 [網站] 節點，然後按一下您想要啟用整合式 Windows 驗證的網站。

8. 中央窗格的標題會變更為您所選取的網站名稱。 在這個窗格中，按兩下 [IIS] 標題下的 [驗證]。

     窗格的標題會變更為 [驗證]。

9. 在 [驗證] 窗格內的 [名稱] 一欄中，以滑鼠右鍵按一下 [Windows 驗證]，然後按一下 [啟用]。

10. 關閉 [Internet Information Services (IIS) 管理員] 視窗。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Microsoft 摘要式驗證](/windows/win32/secauthn/microsoft-digest-authentication)
- [在 Windows Vista 上使用 IIS 7.0 和 Visual Studio 執行 Web 應用程式](/previous-versions/aa964620(v=vs.140))
