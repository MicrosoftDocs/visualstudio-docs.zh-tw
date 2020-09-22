---
title: 如何：建立。從現有的 .vsct 檔案。.Ctc 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838899"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>如何：從現有的 .ctc 檔建立 .vsct 檔
您可以從現有命令資料表 .ctc 原始程式檔建立 XML .vsct 檔。 這樣做，您可以充分利用新的 XML [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 命令資料表 (VSCT) 編譯器格式。  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>從 .ctc 檔建立 .vsct 檔  
  
1. 取得一份 Perl 語言。  
  
2. 取得 Perl 腳本 ConvertCTCToVSCT.pl 的複本，通常位於 *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Tools\bin 資料夾中。  
  
3. 取得一份您想要轉換的 .ctc 原始程式檔。  
  
4. 將檔案放置在相同的目錄中。  
  
5. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [命令提示字元] 視窗中，巡覽至該目錄。  
  
6. 類型  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     其中，PkgCmd.ctc 是 .ctc 檔的名稱，而 PkgCmd.vsct 是您要建立之 vsct 檔的名稱。  
  
     這會建立新的 .vsct XML 命令資料表原始程式檔。 您可以像是處理任何其他 .vsct 檔一樣，使用 Vsct.exe (VSCT 編譯器) 編譯此檔案。  
  
    > [!NOTE]
    > 您可以重新格式化 XML 註解來改善 .vsct 檔的可讀性。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立。.Vsct 檔案](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)