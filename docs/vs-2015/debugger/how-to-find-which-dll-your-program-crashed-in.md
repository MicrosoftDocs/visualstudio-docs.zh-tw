---
title: 如何： 尋找程式損毀的所在的 DLL |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7af6940de5bd4e39451f44176f5c15d2e8b4548
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778393"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>如何：尋找程式損毀時所在的 DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

附註]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
 如果您的應用程式在呼叫系統 DLL 或其他程式碼時損毀，您就必須找出發生損毀時作用中的 DLL。 如果您遇到程式以外的 DLL 中的損毀，您可以識別位置使用**模組**視窗。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>若要使用模組視窗來尋找毀損之處  
  
1.  記下發生毀損的位址。  
  
2.  在上**偵錯**功能表上，選擇**Windows**，然後按一下**模組**。  
  
3.  在 [**模組**] 視窗中，尋找**地址**資料行。 您可能需要使用捲軸才能看到它。  
  
4.  按一下 **地址**以便依位址排序 Dll 的資料行頂端的按鈕。  
  
5.  瀏覽此排序清單，找出位址範圍包含毀損位置的 DLL。  
  
6.  看看**名稱**並**路徑**若要查看的 DLL 名稱和路徑的資料行。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 偵錯原生 Dll](../debugger/how-to-debug-native-dlls.md)   
 [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)





