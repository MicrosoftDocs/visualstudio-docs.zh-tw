---
title: 選項對話方塊、專案和解決方案、建置並執行 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9669437ff47bc141c898a61c055b3a0de8d5d235
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189289"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>選項對話方塊, 專案和方案, 建置和執行
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
在此對話方塊中，您可以指定可同時建置的 Visual C++ 或 Visual C# 專案最大數目、特定的預設建置行為，和一些建置記錄檔設定。 若要開啟 **選項**對話方塊方塊中，選擇**工具**，**選項**功能表列上。 若要存取此組選項，依序展開**專案和方案**，然後選擇**建置並執行**。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **平行專案組建的最大數目**  
 指定可同時建置的 Visual C++ 和 Visual C# 專案的最大數目。 若要最佳化建置程序，平行專案組建的最大數目會自動設定為您電腦的 CPU 數目。 最大值是 32。  
  
 **僅在執行時建置啟始專案和相依性**  
 如果當您選擇 F5 鍵，選取此核取方塊，則會建置啟始專案和其相依性選擇**偵錯**，**開始**功能表中的列，或選擇**建置**，**建置**功能表列上。 如果當您選擇 F5 鍵; 清除此核取方塊，則是會建置所有專案、 相依性和方案檔選擇**偵錯**，**開始**功能表中的列，或選擇**建置**，**建置**功能表列上。 預設會清除這個選項。  
  
 **執行時 (當專案過期時)**  
 > [!NOTE]
>  此清單只適用於 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 專案。  
  
 根據預設，當出現訊息已過期，當您選擇 F5 鍵或選擇的專案組態**偵錯**，**開始**功能表列上。 您可以指定是否依然要建置專案，以及是否顯示此訊息。 使用此選項來指定是否顯示訊息，以及建置行為在不顯示訊息時應該為何。  
  
 **永遠建置**  
 不會顯示訊息方塊，且儘管組態過時也會建置專案。 當您選取時，這個選項會設定**不要再顯示此對話方塊**在訊息方塊，然後選擇**是** 按鈕。  
  
 **永不建置**  
 不會顯示訊息方塊，且不會建置專案。 當您選取此選項設定**不要再顯示此對話方塊**在訊息方塊，然後選擇**No**  按鈕。  
  
 **若要建置的提示字元**  
 每次專案組態過期時便顯示訊息方塊。  
  
 **執行時 (當發生建置或部署錯誤時)**  
 如果發生建置錯誤，當您啟動組建**建置** 功能表中，會出現一個訊息。 您可以指定是否要繼續啟動應用程式，以及每次發生建置錯誤時是否顯示訊息。 使用此選項來指定是否顯示訊息，以及行為在不顯示訊息時應該為何。  
  
> [!NOTE]
>  此選項只適用於 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 專案。  
  
 **若要啟動的提示字元**  
 每次發生建置錯誤時便顯示訊息方塊。  
  
 **不啟動**  
 不會顯示訊息方塊，且不會啟動應用程式。 當您選取此選項設定**不要再顯示此對話方塊**訊息方塊的核取方塊，然後選擇**No**  按鈕。  
  
 **啟動舊版本**  
 不會出現訊息方塊，且不會啟動應用程式的新建置版本。 當您選取時，這個選項會設定**不要再顯示此對話方塊**訊息方塊的核取方塊，然後選擇**是** 按鈕。  
  
 **對新解決方案使用目前選取的專案作為啟始專案**  
 如果選取此核取方塊，新方案會使用目前選取的專案做為啟始專案。  
  
 **MSBuild 專案組建輸出詳細資訊**  
 決定建置的 [輸出] 視窗顯示多少資訊。  
  
 **MSBuild 專案組建記錄檔詳細資訊**  
 > [!NOTE]
>  此選項只適用於 Visual C++ 專案。  
  
 決定多少資訊會寫入建置記錄檔，其位置在 \\...\\*專案名稱*\Debug\\*專案名稱*.log。  
  
## <a name="see-also"></a>另請參閱  
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)



