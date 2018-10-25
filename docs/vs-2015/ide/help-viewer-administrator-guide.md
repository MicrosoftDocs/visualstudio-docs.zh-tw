---
title: Help Viewer 系統管理員指南 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f470c55b08cc559e481ed75e962fda4f0e625a5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871286"
---
# <a name="help-viewer-administrator-guide"></a>說明檢視器系統管理員指南
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

不管使用或不使用網際網路存取，說明檢視器可讓您管理網路環境的本機說明安裝。 本機說明內容會設定為以每台機器為基礎。 根據預設，使用者必須擁有系統管理員權限，以更新其本機說明安裝。  
  
 如果您的網路環境可讓用戶端存取網際網路，說明檢視器可讓您使用命令列指令碼部署來自網際網路的本機說明內容。  
  
 如果您的網路環境不允許用戶端存取網際網路，說明檢視器可以部署從內部網路或網路共用的本機說明內容。 您也可以使用登錄機碼覆寫來停用 Visual Studio IDE 說明選項，例如上線/離線說明內容、第一次啟動 IDE 時的內容安裝、指定內部網路內容服務以及管理內容。  
  
 基本的語法如下：  
  
 \<*通往*> \HlpCtntmgr.exe /operation \<*引數*> /catalogname \<*名稱*> /locale \< *的地區設定*> /sourceuri \< *.msha 路徑或 URL*>  
  
 如需 HlpCtntMgr.exe 命令列語法的詳細資訊，請參閱 [Help Content Manager 的命令列引數](../ide/command-line-arguments-for-the-help-content-manager.md)。  
  
 如需有關建立內容、建立內部網路服務端點以及類似活動類型的詳細資訊，請參閱說明檢視器 SDK。  
  
## <a name="deploying-local-help-content-from-the-internet"></a>部署來自網際網路的本機說明內容  
 您可以使用 MSDN 內容封裝服務，從網際網路部署本機說明內容到用戶端電腦。 使用下列語法：  
  
 \\<*通往*> \v2.2\HlpCtntmgr.exe /operation \<*名稱*> /catalogname \<*目錄名稱*> /locale \< *地區設定*>  
  
 如需 HlpCtntMgr.exe 命令列語法的詳細資訊，請參閱 [Help Content Manager 的命令列引數](../ide/command-line-arguments-for-the-help-content-manager.md)。  
  
 需求：  
  
- 用戶端電腦必須能夠存取網際網路。  
  
- 在安裝本機說明內容後，使用者必須擁有系統管理員權限，以更新、新增或移除本機說明內容。  
  
  警告：  
  
- 說明的預設來源仍處於線上。  
  
  > [!TIP]
  >  您可以修改  HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp 登錄機碼，變更說明的預設來源。 如需詳細資訊，請參閱 [Help Content Manager 覆寫設定](../ide/help-content-manager-overrides.md)。  
  
- 用戶端仍會提示您在第一次啟動 Visual studio 時安裝基本的說明內容。 您可以修改  HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection 登錄機碼，以停用此提示。  
  
### <a name="example"></a>範例  
 以下範例將安裝 Visual Studio 的英文內容到用戶端電腦。  
  
##### <a name="to-install-english-content-from-the-internet"></a>從網際網路安裝英文內容  
  
1.  選擇 [開始]，然後選擇 [執行]。  
  
2.  輸入下列命令：  
  
     C:\Program Files (x86)\Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us  
  
3.  請按 ENTER 鍵。  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>部署用戶端電腦上預先安裝的本機說明內容  
 您可以從線上安裝一組內容到一部電腦上，並接著將該組已安裝的內容複製到其他電腦。  
  
 需求:  
  
- 您安裝該組內容的電腦必須能夠存取網際網路。  
  
- 在安裝本機說明內容後，使用者必須擁有系統管理員權限，以更新、新增或移除本機說明內容。  
  
  > [!TIP]
  >  如果使用者沒有系統管理員權限，建議您停用說明檢視器中的 [管理內容] 索引標籤。 如需詳細資訊，請參閱 [Help Content Manager 覆寫設定](../ide/help-content-manager-overrides.md)。  
  
  警告：  
  
- 如果使用者沒有系統管理員權限，建議您停用說明檢視器中的 [管理內容] 索引標籤。 如需詳細資訊，請參閱 [Help Content Manager 覆寫設定](../ide/help-content-manager-overrides.md)。  
  
- 說明的預設來源仍處於線上。  
  
- 用戶端仍會提示您在第一次啟動 Visual studio 時安裝基本的說明內容。 如需詳細資訊，請參閱 [Help Content Manager 覆寫設定](../ide/help-content-manager-overrides.md)。  
  
### <a name="create-the-content-set"></a>建立內容集  
 在您可以建立基底內容集之前，您必須先解除安裝目標電腦上的所有本機 Visual Studio 內容。  
  
##### <a name="to-uninstall-local-help"></a>解除安裝本機說明  
  
1. 在 Help Viewer 中，選擇 [管理內容] 索引標籤。  
  
2. 底下**可用的文件**，巡覽至 Visual Studio 文件集。  
  
3. 選擇每個子項目旁的 [移除]。  
  
4. 選擇**啟動**解除安裝  
  
5. 瀏覽至*n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 並確認該資料夾只包含檔案 catalogType.xml。  
  
   一旦移除了所有先前安裝的本機 Visual Studio 說明內容，您已準備好下載基底內容集。  
  
##### <a name="to-download-the-content"></a>下載內容  
  
1. 在 Help Viewer 中，選擇 [管理內容] 索引標籤。  
  
2. 底下**可用的文件**，瀏覽至您想要下載，然後選擇 文件集**新增**。  
  
3. 選擇 [開始]。  
  
   接下來，您必須封裝內容，讓它可以部署到用戶端電腦。  
  
##### <a name="to-package-the-content"></a>封裝內容  
  
1.  建立複製內容的目標資料夾，以便稍後進行部署。  
  
     例如： c:\VS12Help。  
  
2.  以系統管理員權限開啟 cmd.exe。  
  
3.  巡覽至您在步驟 1 中建立的資料夾。  
  
4.  輸入下列命令：  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \< *foldername*> \ /y /e /k /o  
  
     例如： `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`  
  
### <a name="deploying-the-content"></a>部署內容  
  
##### <a name="to-deploy-the-content"></a>部署內容  
  
1.  建立網路共用，並將這些說明內容複製到該位置。  
  
     例如，將其內容複製到 c:\VS12Help 中\\\myserver\VS12Help。  
  
2.  建立 .bat 檔案，以包含說明內容的部署指令碼。 由於用戶端在推送的部分過程中要刪除的檔案可能有讀取鎖定，您應該在推送更新之前關閉用戶端。  
  
     例如：  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  在要安裝說明內容的本機電腦上執行批次檔。  
  
## <a name="see-also"></a>另請參閱  
 [Help Content Manager 的命令列引數](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Help Content Manager 覆寫設定](../ide/help-content-manager-overrides.md)



