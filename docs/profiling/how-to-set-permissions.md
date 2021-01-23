---
title: 設定權限 | Microsoft Docs
description: 瞭解電腦的系統管理員如何將程式碼剖析所需的安全性許可權，授與沒有系統管理員許可權的使用者或群組。
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2ab51b317164b8f2e828e0327021fb595574583c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721992"
---
# <a name="how-to-set-permissions"></a>如何：設定權限

本文說明電腦的系統管理員如何將分析所需的安全性權限，授與在該電腦上沒有系統管理員權限的使用者或群組。

基本的安全性原則就是，應用程式應該以不超過所需的權限來執行。 此原則也適用於使用者。 如果使用者不必是 Administrators 群組的成員，只要登入身分是 Users 群組的成員就可以正常工作，那麼就不應該授與他們系統管理員權限。 第一個程序，「建立具有使用者權限的使用者」，說明如何建立身分為 Users 群組成員的使用者帳號。

Users 群組的成員會需要存取磁碟上，與這個小組中之其他成員共用的資料夾和檔案。 第二個程序，「授與共用專案檔的存取權限」，說明如何授與此存取權限。

如果系統管理員將或程式碼剖析工具軟體驅動程式的存取權限授與 Users 群組的成員，他們就可以執行這個程式碼剖析工具。 最後一個程序，「授與剖析工具驅動程式的存取權限」，說明如何授與此驅動程式的存取權限。

> [!NOTE]
> 您必須具有系統管理員權限，才能執行這些程序中的步驟。

## <a name="to-create-a-user-account-that-has-user-permissions"></a>建立具有使用者權限的使用者帳戶

1. 以滑鼠右鍵按一下 **我的電腦** ，然後按一下 [ **管理**]。

     [電腦管理]  視窗隨即開啟。

2. 展開 **[本機使用者和群組]**。

3. 以滑鼠右鍵按一下 [使用者] 資料夾，然後按一下 [新增使用者]。

     [新增使用者] 對話方塊隨即出現。

4. 將您要建立之使用者帳戶的資訊填入這個對話方塊中的欄位。 指定密碼。 或者，選取要求使用者必須在下次登入時變更密碼的核取方塊。

5. 按一下 [ **建立** ]，然後按一下 [ **關閉**]。

     新使用者會出現在 Users 群組中，而這個群組內的使用者並不具有 Administrator 權限。

## <a name="to-grant-access-to-shared-project-files"></a>授與共用專案檔的存取權限

1. 在 Windows 檔案總管 (或檔案總管) 中，找出專案檔 (由這位使用者所使用且由專案小組共用) 資料夾樹狀目錄的根目錄。

     這個資料夾的路徑可能會像下列所示：

    ```cmd
    D:\ourProject
    ```

2. 以滑鼠右鍵按一下此資料夾，然後按一下 [屬性]。

     [ **\<folder name> 屬性**] 對話方塊隨即出現。

3. 按一下 [安全性]  索引標籤。

4. 按一下 [群組或使用者名稱] 方塊中的使用者帳號名稱。

5. 在 [**許可權 \<user name>** ] 方塊中，選取 [**完全控制**] 的核取方塊。

6. 按一下 [確定]。

     如此便會將共用之資料夾樹狀目錄 (從步驟 5 中選取的資料夾開始) 的權限授與使用者。

## <a name="to-grant-access-to-the-profiling-driver"></a>授與程式碼剖析驅動程式的存取權限

1. 以系統管理員身分開啟命令提示字元。

2. 變更目錄至以下路徑：

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. 執行以下命令：

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     這個命令會安裝並啟動程式碼剖析工具的驅動程式。

     這個命令會啟動程式碼剖析驅動程式和服務，讓非系統管理員使用者可以使用自己的使用者處理序空間中提供的程式碼剖析功能。 只有系統管理員可以執行此命令；如果執行者是非系統管理員使用者，此命令將會失敗。

     請注意，除非您也執行這個程序中的最後步驟，否則這個步驟的效果會在電腦重新啟動後消失。

4. 執行以下命令，允許在該電腦上沒有系統管理員存取權的使用者或群組存取程式碼剖析驅動程式功能：

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     此命令會授與或帳戶對程式碼 \<user name> \<group name> 剖析工具的存取權。 \<right>選項會決定使用者可以存取的程式碼剖析功能。 \<right>選項可以是下列一或多個值：

    - FullAccess - 允許存取所有程式碼剖析方法，包括從服務收集效能資料、取樣和跨工作階段進行程式碼剖析。

    - SampleProfiling - 允許存取取樣程式碼剖析方法。

    - CrossSession -允許存取跨工作階段程式碼剖析，這是對服務進行程式碼剖析所需要的權限。

5. (選擇性) 若要在電腦重新啟動後保留前述任一步驟的結果，請執行下列命令：

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   指定的使用者登入之後，不需要有系統管理員權限就可以使用程式碼剖析工具。

## <a name="see-also"></a>另請參閱

[設定效能會話](../profiling/configuring-performance-sessions.md) 
[>vsperfcmd](../profiling/vsperfcmd.md) 
[分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)
