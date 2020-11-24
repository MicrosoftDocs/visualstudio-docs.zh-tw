---
title: 建立用於測試的診斷資料配接器
description: 瞭解如何使用 Visual Studio Enterprise 內提供的 Api 撰寫程式碼，以在測試回合的特定點執行工作。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e73942509ca39d845c2a79f616ace311651be006
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440268"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>建立診斷資料配接器以收集自訂資料或影響測試電腦

您可以建立自己的診斷資料配接器以在執行測試時收集資料，或直接影響測試電腦做為測試的一部分。 例如，您可以收集由待測應用程式所建立的記錄檔，並將該記錄檔附加至測試結果中，或者是在遇到電腦剩下不多磁碟空間的情況時執行測試。 您可以使用 Visual Studio Enterprise 內提供的 API，撰寫程式碼以執行測試回合中特定點的工作。 例如，您可以在測試回合啟動時、每個個別測試執行之前與之後，以及測試回合完成時執行工作。

::: moniker range="vs-2017"
您可以使用組態設定檔為您自訂的診斷資料配接器提供預設輸入。 例如，您可以提供有關要收集並附加至測試結果的檔案之位置，或是您要在系統上保留多少磁碟空間的資訊。 您可以針對您所建立的每項測試設定，來設定這些資料。 您可以使用 Microsoft Test Manager 隨附的預設編輯器來顯示和編輯這些資料，或建立您自己的使用者控制項作為編輯器使用。 您在編輯器中對配接器組態所做的任何變更，都會儲存在測試設定中。
::: moniker-end

::: moniker range=">=vs-2019"
您可以使用組態設定檔為您自訂的診斷資料配接器提供預設輸入。 例如，您可以提供有關要收集並附加至測試結果的檔案之位置，或是您要在系統上保留多少磁碟空間的資訊。 您可以針對您所建立的每項測試設定，來設定這些資料。 您可以建立自己的使用者控制項作為編輯器使用。 您在編輯器中對配接器組態所做的任何變更，都會儲存在測試設定中。
::: moniker-end

如果您要從 Visual Studio 執行測試，則必須將這些測試設定設為作用中。 如需測試設定的詳細資訊，請參閱 [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>工作

下列主題可協助您建立診斷資料配接器：

|工作|相關主題|
|-|-----------------------|
|**建立診斷資料配接器：** 您可以藉由建立類別庫來建立診斷資料配接器，然後使用診斷資料配接器 API，收集您想要的資訊或影響您用來執行測試的測試系統。|-   [如何：建立診斷資料介面卡](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**選取執行測試時要使用的自訂診斷資料配接器：** 您可以選取要用於測試設定的診斷資料配接器，以便在執行測試時使用該配接器。|-   [在測試時收集診斷資料 (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)<br />-   [在手動測試中收集診斷資料 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)|

## <a name="see-also"></a>另請參閱

- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)