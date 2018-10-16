---
title: 如何： 建立。從現有的 Vsct 檔案。Cto 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 82cf711d33b3b3ca5150378e7111a2a21c8c03cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235738"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>如何：從現有的 .Cto 檔建立 .Vsct 檔
您可以從現有的二進位檔 .cto 建立 XML 檔 .vsct。 這樣做可讓您充分利用新的命令資料表編譯器格式。 即使 .cto 檔是從 .ctc 檔所編譯，這個程序也適用。 您可以將 .vsct 檔編輯並編譯成另一個 .cto 檔。  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>從 .cto 檔建立 .vsct 檔  
  
1.  取得 .cto 檔案和其對應 .ctsym 檔的複本。  
  
2.  將檔案放入與 vsct.exe 編譯器所在相同的目錄。  
  
3.  在 Visual Studio 命令提示字元中，移至包含 .cto 和 .ctsym 檔的目錄。  
  
4.  輸入 **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct -S**_symfilename_**.ctsym**。  
  
     `ctofilename` 是 .cto 檔的名稱，`vsctfilename` 是您要建立之 vsct 檔的名稱，而 `symfilename` 是 .ctsym 檔的名稱。  
  
     這個程序會建立新的 .vsct XML 命令資料表編譯器檔案。 您可以像是處理任何其他 .vsct 檔一樣，使用 vsct 編譯器 vsct.exe 編輯及編譯此檔案。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立。Vsct 檔案](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)