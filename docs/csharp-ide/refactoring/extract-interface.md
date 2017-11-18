---
title: "擷取介面-重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 55e17f0a-eacb-41ec-b8ca-74f5c6bbd6de
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: csharp
ms.openlocfilehash: 854e341a5c02b3bb4b0a596720a4899410550689
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="extract-an-interface-in-c"></a>擷取在 C# 介面 #
**項目：**可讓您建立使用現有的成員，從類別、 結構或介面的介面。

**當：**您有數個類別、 結構或介面可能會進行一般由其他類別、 結構或介面的方法。

**原因：**介面為物件導向設計絕佳建構。  假設所有可能有通用的方法，例如 Eat，飲料，睡眠狀態的各種動物 （Dog，貓鳥） 的類別。  使用像 IAnimal 的介面，可讓 Dog、 貓和鳥有 「 簽章 」 針對這些方法一般。  

**如何：**

1. 反白顯示要執行的動作，類別名稱，或只文字將游標放在某個位置中的類別名稱。

   ![反白顯示的程式碼](media/extractinterface_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl + R**，然後**Ctrl + I**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**擷取介面**從預覽視窗快顯視窗。
   * **滑鼠**
     * 選取**編輯 > 重構 > 擷取介面**。
     * 以滑鼠右鍵按一下選取的類別名稱**快速控制項目及重構**功能表，然後選取**擷取介面**從預覽視窗快顯視窗。

1. 在**擷取介面**顯的對話方塊中輸入系統要求的資訊：![擷取介面](media/extractinterface_dialog.png)
   | 欄位 | 說明 |
   | --- | --- |
   | **新的介面名稱** | 要建立的介面名稱。 這將會預設為我*ClassName*，其中*ClassName*是您在上面選取之類別的名稱。 |
   | **新的檔案名稱** | 將產生包含檔案的介面名稱。 因為使用的介面名稱，則會預設為我*ClassName*，其中*ClassName*是您在上面選取之類別的名稱。 |
   | **選取 public 成員以形成介面** | 要擷取至介面的項目。  您可以選取 視需要為您想。 |

1. 按一下 [確定]。

   指定之名稱的檔案中，將會立即建立介面。  此外，您所選取的類別現在會實作該介面。

   ![產生的類別](media/extractinterface_class.png)
   ![產生介面](media/extractinterface_interface.png)

## <a name="see-also"></a>另請參閱  
[重構 (C#)](../refactoring-csharp.md)