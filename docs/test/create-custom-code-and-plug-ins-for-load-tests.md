---
title: 為負載測試建立自訂程式碼和外掛程式
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7cd3dbd5e7aeb00c2de1a656c26db3a377b8ffe8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665100"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>為負載測試建立自訂程式碼和外掛程式

自訂外掛程式會使用您撰寫並附加至負載測試或 Web 效能測試內的程式碼。 您可以使用負載測試 API 和 Web 效能測試 API，針對測試建立可擴充至內建功能的自訂外掛程式。 您可以將多個外掛程式新增至負載測試。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-----------------------|
|**針對負載測試建立自訂外掛程式：** 您可以使用負載測試 API 來建立自訂外掛程式，以便將其他測試功能新增至負載測試。|-   [如何：使用負載測試 API](../test/how-to-use-the-load-test-api.md)<br />-   [如何：建立負載測試外掛程式](../test/how-to-create-a-load-test-plug-in.md)|
|**針對 Web 效能測試建立自訂外掛程式：** 您可以使用 Web 效能測試 API 來建立自訂外掛程式，以便將其他測試功能新增至 Web 效能測試 (包括要求層級)。 您也可以建立 Web 服務測試。<br /><br /> 此外，您可以建立 Web 錄製器外掛程式，以便在 Web 效能測試記錄之後但在 [Web 效能測試結果檢視器] 中出現之前，進行修改。|-   [如何：使用 Web 效能測試 API](../test/how-to-use-the-web-performance-test-api.md)<br />-   [如何：建立 Web 效能測試外掛程式](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [如何：建立要求層級外掛程式](../test/how-to-create-a-request-level-plug-in.md)<br />-   [如何：建立 Web 服務測試](../test/how-to-create-a-web-service-test.md)<br />-   [如何：建立錄製器外掛程式](../test/how-to-create-a-recorder-plug-in.md)|
|**將 UI 功能新增至 Web 效能測試結果檢視器：** 您可以使用 Visual Studio 增益集，將其他 UI 功能新增至 Web 效能測試結果檢視器。|-   [如何：建立 Web 效能測試結果檢視器的 Visual Studio 增益集](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**建立自訂 HTTP 內容編輯器：** 您可以建立自訂編輯器，以便編輯來自 Web 服務的二進位或字串 Http XML 回應。|-   [如何：建立 Web 效能測試編輯器的自訂 HTTP 內容編輯器](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>參考資料

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [產生和執行 Web 效能測試程式碼](../test/generate-and-run-a-coded-web-performance-test.md)