---
title: 管理外部工具 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a59432d6b630606ac5c133e8a5811186fcf7c34
ms.sourcegitcommit: 40393347a36779230d128f2355a911632a8d458e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866755"
---
# <a name="managing-external-tools"></a>管理外部工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以從 Visual Studio 內部呼叫外部工具。 [工具] 功能表中有提供一些預設的工具，但您可以另外加入自己的可執行檔。  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Visual Studio 工具功能表上提供的工具  
 您可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的 [工具] 功能表呼叫下列工具。 也可以從 [快速啟動] 視窗以名稱來呼叫工具。 例如，若要呼叫 GuidGen.exe，請鍵入 **Create GUID**。  
  
1.  建立 GUID：產生 GUID。  
  
2.  錯誤查詢：從輸入的值取得錯誤訊息。 如需詳細資訊，請參閱 [ERRLOOK 參考](http://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91)。  
  
3.  ATL/MFC 追蹤工具：顯示 ATL 與 MFC 來源中的偵錯追蹤訊息。  
  
4.  PreEmptive Protection - Dotfuscator：保護 .NET 程式免於反向工程。  
  
5.  SPY++：以圖形化方式顯示處理序、執行緒、視窗及視窗訊息。  
  
6.  WCF 服務組態編輯器：可用以建立及修改 WCF 服務的組態設定。  
  
> [!WARNING]
>  視您安裝的 Visual Studio 版本及套用的設定檔之不同，您看到的外部工具清單或許有些不同。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="adding-new-tools"></a>加入新工具  
 您可將外部工具加入 [工具] 功能表。 開啟 [外部工具] 對話方塊，按一下 [加入]，然後填入資訊。 例如，下列輸入內容會讓 Windows 檔案總管的開啟位置，會是於 Visual Studio 中目前所開啟之檔案所在的目錄：  
  
1.  Title: Open File Location  
  
2.  Command: explorer.exe  
  
3.  Arguments: /root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>外部工具的引數  
 下列引數是您啟動外部工具時指派的 Visual Studio 變數。 可使用 [外部工具] 對話方塊將 [記事本] 或 Spy++ 等外部工具的連結列在 [工具] 功能表上。  
  
> [!NOTE]
>  IDE 狀態列會顯示目前這一行和目前資料行的變數，以指出插入點在作用中程式碼編輯器的位置。 目前的文字變數則會傳回在該位置選取的文字或程式碼。  
  
|名稱|引數|說明|  
|----------|--------------|-----------------|  
|項目路徑|$(ItemPath)|目前檔案的完整檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  
|項目目錄|$(ItemDir)|目前檔案的目錄 (磁碟機 + 路徑)。|  
|項目檔名|$(ItemFilename)|目前檔案的檔案名稱 (檔案名稱)。|  
|項目副檔名|$(ItemExt)|目前檔案的副檔名。|  
|目前的行|$(CurLine)|程式碼視窗中滑鼠游標目前的行位置。|  
|目前的資料行|$(CurCol)|程式碼視窗中滑鼠游標目前的資料行位置。|  
|目前的文字|$(CurText)|選取的文字。|  
|目標路徑|$(TargetPath)|要建置之項目的完整檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  
|目標目錄|$(TargetDir)|要建置之項目的目錄。|  
|目標名稱|$(TargetName)|要建置之項目的檔案名稱。|  
|目標副檔名|$(TargetExt)|要建置之項目的副檔名。|  
|二進位檔目錄|$(BinDir)|正在建置之二進位檔的最終位置 (定義為磁碟機 + 路徑)。 例如：**\\...\My Documents\Visual Studio \<本>\\<專案名稱\>\bin\debug**|  
|專案目錄|$(ProjDir)|目前專案的目錄 (磁碟機 + 路徑)。|  
|專案檔名|$(ProjFileName)|目前專案的檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  
|方案目錄|$(SolutionDir)|目前方案的目錄 (磁碟機 + 路徑)。|  
|方案檔名|$(SolutionFileName)|目前方案的檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  
  
## <a name="see-also"></a>請參閱  
 [C/C++ 建置工具](http://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
