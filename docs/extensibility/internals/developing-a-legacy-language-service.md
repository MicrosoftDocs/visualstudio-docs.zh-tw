---
title: 開發傳統語言服務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708675"
---
# <a name="develop-a-legacy-language-service"></a>開發傳統語言服務
本節連結到可説明您創建舊語言服務的主題。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語言服務的新方法的詳細資訊,請參閱[編輯器和語言服務擴展](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="in-this-section"></a>本節內容
- [傳統語言服務的模型](../../extensibility/internals/model-of-a-legacy-language-service.md)

 為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心編輯器提供最小語言服務的模型。 您可以使用此模型作為創建您自己的語言服務的指南。

- [舊語言服務介面](../../extensibility/internals/legacy-language-service-interfaces.md)

 討論實現語言服務所需的物件,並提供可用於提供語法突出顯示、方法數據和其他功能的其他物件的清單。

- [攔截舊語言服務指令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 描述如何將命令篩選器插入到語言服務中,以攔截文本檢視將處理的命令。

- [註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)

 提供有關如何使用 註冊語言服務[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的資訊 。

- [除錯的語言服務支援](../../extensibility/internals/language-service-support-for-debugging.md)

 描述語言服務如何提供支援調試器的功能。

- [檢查表:建立舊語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 提供用於為核心編輯器創建和整合語言服務的分步說明。

## <a name="related-sections"></a>相關章節
- [舊語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 討論如何在語言服務中實現語法突出顯示。

- [舊語言服務中的敘述完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 討論敘述完成,語言服務幫助使用者完成他們已經開始鍵入的語言關鍵字或元素的過程。

- [舊語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 描述如何為重載函數和方法提供方法提示。

- [如何:在舊語言服務中提供隱藏文字支援](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 解釋隱藏文本區域的用途,並提供有關如何實現隱藏文本區域的說明。

- [如何:在傳統語言服務中提供擴展的大綱支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 解釋將概述對語言的支援擴展到支援「*摺疊到定義」命令的*兩個選項。
