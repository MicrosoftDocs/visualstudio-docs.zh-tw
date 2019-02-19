---
title: HOW TO：針對範本進行疑難排解 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb2c708bfb6bfafe90b548ad2826e0cf11882a3b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793202"
---
# <a name="how-to-troubleshoot-templates"></a>如何：疑難排解範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果範本無法在開發環境中載入，有數種方式可找出問題。  
  
## <a name="validating-the-vstemplate-file"></a>驗證 .vstemplate 檔案  
 如果範本中的 .vstemplate 檔案未遵守 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 範本結構描述，範本可能不會出現在 [新增專案] 對話方塊中。  
  
#### <a name="to-validate-the-vstemplate-file"></a>驗證 .vstemplate 檔案  
  
1.  找出包含樣板的.zip 檔。  
  
2.  將 zip 檔解壓縮。  
  
3.  在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的 [檔案] 功能表上，按一下 [開啟]，然後按一下 [檔案]。  
  
4.  選取範本的 .vstemplate 檔案，然後按一下 [開啟]。  
  
5.  確認 .vstemplate 檔案的 XML 遵守 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 範本結構描述。 如需 .vstemplate 結構描述的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
    > [!NOTE]
    >  撰寫 .vstemplate 檔案時若要取得 IntelliSense 支援，請在 `VSTemplate` 項目中新增 `xmlns` 屬性並為它指派 http://schemas.microsoft.com/developer/vstemplate/2005 值。  
  
6.  儲存並關閉.vstemplate 檔案。  
  
7.  選取包含在範本中的檔案、按一下滑鼠右鍵、選取 [傳送到]，然後按一下 [壓縮的 (zipped) 資料夾]。 您選取的檔案即會壓縮成 .zip 檔。  
  
8.  將新的 .zip 檔放在與舊 .zip 檔相同的目錄中。  
  
9. 刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。  
  
## <a name="monitoring-the-event-log"></a>監視事件記錄檔  
 處理範本 .zip 檔案時遇到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 記錄錯誤。 如果範本不會如預期地顯示在 [新增專案] 對話方塊中，您可以使用 [事件檢視器] 來針對此問題進行疑難排解。  
  
#### <a name="to-locate-template-errors-in-event-viewer"></a>在事件檢視器中找出範本錯誤  
  
1.  在 Windows 中，請依序按一下 [開始] 和 [控制台]，然後依序按兩下 [系統管理工具] 和 [事件檢視器]。  
  
2.  在左窗格中，按一下 [應用程式]。  
  
3.  尋找 **Source** 值為 `Visual Studio - VsTemplate` 的事件。  
  
4.  按兩下範本事件，以檢視錯誤。  
  
## <a name="see-also"></a>請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
