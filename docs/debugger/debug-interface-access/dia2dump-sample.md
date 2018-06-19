---
title: Dia2dump 範例 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5559d1ac2a03eaeb1dca57531cd2f19831851d3b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457822"
---
# <a name="dia2dump-sample"></a>Dia2dump 範例
Dia2dump 範例會隨 Visual Studio 安裝，且含有 Dia2dump.cpp 原始程式檔。 已編譯的可執行檔會從命令列執行，並顯示整個程式資料庫 (.pdb) 檔案的內容。  
  
### <a name="to-install-the-sample"></a>若要安裝範例  
  
1.  請確認您的系統符合所有 Visual Studio 安裝程式起始頁中所述的安裝需求。  
  
2.  安裝 Visual Studio，並遵循隨附範例的所有設定和安裝指示。  
  
#### <a name="to-build-the-sample"></a>若要建置範例  
  
1.  Visual Studio 中開啟 Dia2dump.sln 檔案。 （如有必要，Visual Studio 將先協助您升級 Dia2dump 專案）。  
  
2.  在 專案屬性頁中**C/c + +** &#124; **一般** &#124; **其他 Include 目錄**屬性，指定`..\DIA SDK\include`目錄。 這可確保編譯器可以找到 dia2.h 檔案。  
  
3.  在**建置**功能表上，按一下 **重建方案**。  
  
4.  關閉 Visual Studio。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  開啟命令提示字元並輸入下列命令：  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Dia2dump.cpp 原始程式檔](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [移植、移轉及升級 Visual Studio 專案](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)