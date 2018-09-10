---
title: 錯誤： 偵錯失敗，因為未啟用整合式的 Windows 驗證 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f56cca9fa637efaa66b6dcab4716d4a1900aa61d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44278641"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>錯誤：偵錯失敗，因為整合式 Windows 驗證沒有啟用
因為驗證錯誤，所以無法對要求偵錯之使用者進行驗證。 這種情形可能會在您嘗試逐步執行 Web 應用程式或 XML Web Service 時發生。 造成這個錯誤的原因之一是未啟用整合式 Windows 驗證。 若要啟用該驗證，請遵循「若要啟用整合式 Windows 驗證」內所述的步驟進行。  
  
 如果您已啟用整合式的 Windows 驗證，而且仍然出現這個錯誤，很可能會發生此錯誤，因為**摘要式 Windows 網域伺服器驗證**已啟用。 在此情況下，您應該聯絡網路系統管理員。  
  
### <a name="to-enable-integrated-windows-authentication"></a>若要啟用整合式 Windows 驗證  
  
1.  使用系統管理員帳戶登入 Web 伺服器。  
  
2.  按一下 **開始**，然後按一下**控制台**。  
  
3.  在 **控制台中**，按兩下**系統管理工具**。  
  
4.  按兩下**Internet Information Services**。  
  
5.  按一下 [Web 伺服器] 節點。  
  
     A**網站**資料夾開啟的伺服器名稱之下。  
  
6.  您可以為所有網站或個別網站設定驗證。 若要設定的所有網站的驗證，以滑鼠右鍵按一下**Web Sites**資料夾，然後按一下**屬性**。 若要設定個別網站驗證，請開啟**Web Sites**資料夾中，個別的網站上，以滑鼠右鍵按一下，然後按一下**屬性**。  
  
     **屬性**對話方塊隨即出現。  
  
7.  按一下 [**目錄安全**] 索引標籤。  
  
8.  在 **匿名存取及驗證控制**區段中，按一下**編輯**。  
  
     **驗證方法**對話方塊隨即出現。  
  
9. 底下**驗證存取權**，選取**整合式 Windows 驗證**。  
  
10. 按一下 [ **[確定]** 以關閉**驗證方法**] 對話方塊。  
  
11. 按一下 [ **[確定]** 以關閉**屬性**] 對話方塊。  
  
12. 關閉**Internet Information Services**視窗。  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>若要在 Windows Vista/IIS 7 內啟用整合式 Windows 驗證  
  
1.  使用系統管理員帳戶登入 Web 伺服器。  
  
2.  如果您先前未開啟 [Windows 驗證] 和 [II6 管理相容性]，請遵循下列步驟來執行此動作：  
  
    1.  按一下 **開始**，按一下**控制台**，然後按一下 **程式**。  
  
    2.  底下**程式和功能**，按一下**開啟 Windows 功能開啟或關閉**。  
  
         [使用者帳戶控制] 對話方塊隨即出現，並詢問您是否同意繼續進行。  
  
    3.  按一下 [ **繼續**]。  
  
         [Windows 功能] 對話方塊隨即出現。  
  
    4.  在 [功能] 清單中，展開**Internet Information Services**節點。  
  
    5.  底下**Internet Information Services**，展開**World Wide Web 服務**節點。  
  
    6.  底下**World Wide Web 服務**，按一下**安全性**。  
  
    7.  按一下  **Windows 驗證**。  
  
    8.  底下**Internet Information Services**，展開**Web 管理工具**節點。  
  
    9. 底下**Web 管理工具**，展開**IIS 6 管理相容性**節點，然後選取**IIS 6 Metabase 及 IIS 6 設定相容性**核取方塊。  
  
    10. 底下**Web 管理工具**，選取**IIS 管理主控台**按一下 **[確定]。**  
  
    11. 重新啟動電腦，這些變更就會生效。  
  
3.  按一下 **開始**，然後按一下**控制台**。  
  
4.  按一下 **傳統檢視**，然後按兩下**系統管理工具**。  
  
5.  在 **名稱**資料行，然後按兩下**Internet Information Services (IIS) 管理員**。  
  
6.  在 [**連線**] 欄中，展開伺服器節點。  
  
     A**網站**資料夾開啟的伺服器名稱之下。  
  
7.  依序展開**網站**節點，按一下您要啟用整合式的 Windows 驗證的網站。  
  
8.  中央窗格的標題會變更為您所選取的網站名稱。 在此窗格中，在**IIS**標題之下，連按兩下**驗證**。  
  
     窗格的標題會變更為**驗證**。  
  
9. 在**驗證**窗格，請在**名稱**資料行，以滑鼠右鍵按一下**Windows 驗證**然後按一下**啟用**。  
  
10. 關閉**Internet Information Services (IIS) 管理員**視窗。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯的 Web 應用程式： 錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft 摘要式驗證](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [執行 Windows Vista 與 IIS 7.0 上的 Web 應用程式與 Visual Studio](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)