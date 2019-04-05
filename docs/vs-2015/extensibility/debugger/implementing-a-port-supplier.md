---
title: 實作連接埠提供者 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930737"
---
# <a name="implementing-a-port-supplier"></a>實作連接埠提供者
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

連接埠提供者會提供工作階段的偵錯管理員 (SDM) 的要求上的連接埠。 連接埠提供者必須對非 DCOM 機器偵錯時，或當新的裝置必須支援實作。 比方說，若要提供對手機偵錯，您可以實作連接埠提供者，提供行動電話 （或許是藉由連線到 IR 或儲存格連接），並列舉的處理程序和手機上執行的程式的連接埠。  
  
 對於以 Windows 為基礎的電腦 （包括遠端偵錯） 上的偵錯程式，Visual Studio 會提供原生和 Common Language Runtime (CLR) 處理程序的連接埠提供者，這樣就不需要在這些情況下實作您自己的連接埠提供者。  
  
## <a name="in-this-section"></a>本節內容  
 [實作和註冊連接埠提供者](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 討論在 SDM 與連接埠提供者和它的連接埠的互動方式。  
  
 [必要的連接埠提供者介面](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 文件以取得連接埠提供者必須實作的介面。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
