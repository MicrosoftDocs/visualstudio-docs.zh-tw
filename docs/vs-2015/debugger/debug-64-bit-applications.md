---
title: Debug 64 位應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0eaa719bb3eeca2eb3dfe558184699ccca42819
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387196"
---
# <a name="debug-64-bit-applications"></a>偵錯 64 位元應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新版本可在[Debug 64 位應用程式](/visualstudio/debugger/debug-64-bit-applications)中找到。  
  
您可以對本機電腦或遠端電腦上執行的 64 位元應用程式進行偵錯。  
  
 若要對遠端電腦上執行的 64 位元應用程式進行偵錯，請參閱 [Remote Debugging](../debugger/remote-debugging.md)。  
  
 若要在本機偵錯 64 位元應用程式，Visual Studio 會使用 64 位元背景工作處理序 (msvsmon.exe) 來執行無法在 32 位元 Visual Studio 處理序內完成的低階作業。  
  
 使用 .NET Framework 3.5 (含) 以前版本的 64 位元處理序不支援混合模式偵錯。  
  
## <a name="debug-a-64-bit-application"></a>偵錯 64 位元應用程式  
 若要嘗試偵錯 64 位元應用程式：  
  
1. 建立 Visual Studio 方案，例如 C# 主控台應用程式。  
  
2. 使用組態管理員將組態設定為 64 位元。 如需詳細資訊，請參閱 [How to: Configure Projects to Target Platforms](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
3. 此時會啟動 64 位元版本的遠端偵錯工具 (msvsmon.exe)。 只要開啟具有 64 位元組態的方案，就會執行此工具。  
  
4. 開始偵錯。 您應該會與 32 位元組態有相同的體驗。 如果您收到錯誤，請參閱下列＜疑難排解＞一節。  
  
## <a name="troubleshooting-64-bit-debugging"></a>64 位元偵錯疑難排解  
 您可能會看到錯誤：「64 位元偵錯作業所花的時間超出預期」。 在此情況下，Visual Studio 已傳送要求到 64 位元版本的 msvsmon.exe，但該要求的結果卻花很長的時間傳回。  
  
 此錯誤的主要原因有兩個：  
  
- 電腦上所安裝的網路安全性軟體造成網路堆疊不可靠，因此已丟棄通過 localhost 的封包。 請嘗試停用所有網路安全性軟體，看看這樣做是否可以解決問題。 如果是，請將軟體干擾 localhost 流量的情形回報給您的網路安全性軟體廠商。  
  
- 您遇到 Visual Studio 停止回應或其他效能問題的問題。 如果此問題經常發生，您可以收集 Visual Studio 的傾印 (devenv.exe) 和背景工作處理序 (msvsmon.exe)，然後傳送給 Microsoft。 
  
## <a name="see-also"></a>另請參閱  
 [64位應用程式](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [正在設定64位的程式](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Visual Studio IDE 64 位支援](../ide/visual-studio-ide-64-bit-support.md)   
 [使用傾印檔案](../debugger/using-dump-files.md)   
 [遠端偵錯](../debugger/remote-debugging.md)
