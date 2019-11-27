---
title: 將追蹤屬性加入至網域指定的語言定義 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19d673d9d09ce95580e25033966e1a901255fd90
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292647"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>在網域指定的語言定義中加入追蹤屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何將追蹤屬性加入至領域模型。

 *追蹤定義域*屬性是使用者可以更新的屬性，但其預設值是使用其他定義域屬性或專案的值來計算。

 例如，在特定領域語言工具（DSL 工具）中，網域類別的 [顯示名稱] 屬性具有使用網域類別的名稱來計算的預設值，但使用者可以在設計階段變更值，或將它重設為計算值。

 在此逐步解說中，您會根據模型的 [預設命名空間] 屬性，建立具有命名空間追蹤屬性的特定領域語言（DSL）。 如需追蹤屬性的詳細資訊，請參閱[定義追蹤屬性](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be)。

- DSL 工具支援追蹤屬性描述項。 不過，DSL 設計工具無法用來將追蹤屬性新增至語言。 因此，您必須加入自訂程式碼來定義和執行追蹤屬性。

  追蹤屬性有兩個狀態： [追蹤] 和 [已更新使用者]。 追蹤屬性具有下列功能：

- 當處於追蹤狀態時，會計算追蹤屬性的值，而值會隨著模型中的其他屬性變更而更新。

- 當在使用者狀態更新時，追蹤屬性的值會保留使用者上次設定屬性的值。

- 在 [**屬性**] 視窗中，只有當屬性位於 [已更新的使用者] 狀態時，才會啟用 [追蹤] 屬性的 [**重設**] 命令。 **Reset**命令會將追蹤屬性狀態設定為追蹤。

- 在 [**屬性**] 視窗中，當追蹤屬性處於追蹤狀態時，其值會以一般字型顯示。

- 在 [**屬性**] 視窗中，當追蹤屬性位於 [已更新的使用者] 狀態時，其值會以粗體字顯示。

## <a name="prerequisites"></a>必要條件
 開始進行本逐步解說之前，您必須先安裝下列元件：

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](https://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](https://go.microsoft.com/fwlink/?LinkID=185580)|
|[!INCLUDE[dsl](../includes/dsl-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](https://go.microsoft.com/fwlink/?LinkID=185581)|

## <a name="creating-the-dsl-project"></a>建立 DSL 專案
 針對您的特定領域語言建立專案。

#### <a name="to-create-the-project"></a>若要建立專案

1. 建立特定領域語言設計工具專案。 將它命名為 `TrackingPropertyDSL`。

2. 在 [**網域指定的語言設計工具]** 中，設定下列選項：

    1. 選取 [ **MinimalLanguage** ] 範本。

    2. 使用特定領域語言的預設名稱，`TrackingPropertyDSL`。

    3. 將模型檔案的副檔名設定為 `trackingPropertyDsl`。

    4. 使用模型檔案的預設範本圖示。

    5. 將產品的名稱設定為 `Product Name`。

    6. 將公司名稱設定為 `Company Name`。

    7. 針對方案中的專案，使用根命名空間的預設值，`CompanyName.ProductName.TrackingPropertyDSL`。

    8. 允許嚮導為您的元件建立強式名稱金鑰檔。

    9. 查看解決方案的詳細資料，然後按一下 **[完成]** 以建立 DSL 定義專案。

## <a name="customizing-the-default-dsl-definition"></a>自訂預設 DSL 定義
 在本節中，您會自訂 DSL 定義以包含下列專案：

- 模型中每個專案的命名空間追蹤屬性。

- 模型中每個元素的布林 IsNamespaceTracking 屬性。 這個屬性會指出追蹤屬性是處於追蹤狀態，還是在使用者狀態更新。

- 模型的預設命名空間屬性。 這個屬性將用來計算命名空間追蹤屬性的預設值。

- 模型的 CustomElements 計算屬性。 這個屬性會指出具有自訂命名空間的元素比例。

#### <a name="to-add-the-domain-properties"></a>新增網域屬性

1. 在 DSL 設計工具中，以滑鼠右鍵按一下 [ **examplemodel.store.customer** ] 網域類別，指向 [**新增**]，然後按一下 [ **DomainProperty**]。

    1. 將新的屬性命名為 `DefaultNamespace`。

    2. 在新屬性的 [**屬性**] 視窗中，將 [**預設值**] 設定為 `DefaultNamespace`，並將 [**類型**] 設定為 [**字串**]。

2. 在**examplemodel.store.customer**網域類別中，新增名為 `CustomElements`的網域屬性。

     在新屬性的 [**屬性**] 視窗中，將 [**類型**] 設定為 [**計算**]。

3. 在**ExampleElement**網域類別中，新增名為 `Namespace`的網域屬性。

     在新屬性的 [**屬性**] 視窗中，將 [**可流覽**] 設定為 [ **False**]，並將 [**類型**] 設定為**CustomStorage**。

4. 在**ExampleElement**網域類別中，新增名為 `IsNamespaceTracking`的網域屬性。

     在新屬性的 **屬性** 視窗中，將 **可流覽** 設定為  **False**，將 **預設值** **設定為** `true`，並將 **類型** 設定為

#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>更新圖表元素和 DSL 詳細資料

1. 在 [DSL 設計工具] 中，以滑鼠右鍵按一下 [ **ExampleShape** geometry] 圖形，指向 [**加入**]，然後按一下 [**文字**裝飾專案]。

    1. 將新的文字裝飾專案命名為 `NamespaceDecorator`。

    2. 在文字裝飾專案的 [**屬性**] 視窗中，將 [**位置**] 設定為**InnerBottomLeft**。

2. 在 [DSL 設計工具] 中，選取將**ExampleElement**類別連接至 [ **ExampleShape** ] 圖形的線條。

    1. 在 [ **DSL 詳細資料**] 視窗中，選取 [裝飾專案**對應**] 索引標籤。

    2. 在 [**裝飾專案**] 清單中，選取 [ **NamespaceDecorator**]，選取其核取方塊，然後在 [**顯示內容**] 清單中，選取 [**命名空間**]。

3. 在 [ **DSL Explorer**] 中，展開 [**網域類別**] 資料夾，以滑鼠右鍵按一下 [ **ExampleElement** ] 節點，然後按一下 [**加入新的定義欄位型別描述**元]。

    1. 展開 [ **ExampleElement** ] 節點，然後選取 [**自訂類型描述項（網欄位型別描述項）** ] 節點。

    2. 在網欄位型別描述元的 [**屬性**] 視窗中，將 [**自訂編碼**] 設定為**True**。

4. 在 [ **DSL Explorer**] 中，選取 [ **Xml 序列化行為**] 節點。

    1. 在 [**屬性**] 視窗中，將 [**自訂 Post 載入**] 設定為 [ **True**]。

## <a name="transforming-templates"></a>轉換範本
 現在您已定義 DSL 的網域類別和屬性，您可以確認 DSL 定義可以正確轉換，以重新產生專案的程式碼。

#### <a name="to-transform-the-text-templates"></a>轉換文字模板

1. 在 [**方案總管**] 工具列上，按一下 [**轉換所有範本**]。

2. 系統會重新產生解決方案的程式碼，並儲存 Dsldefinition.dsl 檔。 如需定義檔之 XML 格式的詳細資訊，請參閱[dsldefinition.dsl 檔。](../modeling/the-dsldefinition-dsl-file.md)

## <a name="creating-files-for-custom-code"></a>建立自訂程式碼的檔案
 當您轉換所有範本時，系統會產生原始程式碼，以在 Dsl 和 DslPackage 專案中定義您的特定領域語言。 為了避免干擾產生的文字，請在檔案中撰寫自訂程式碼，而這些檔案與產生的程式碼檔案不同。

 您必須提供程式碼來維護追蹤屬性的值和狀態。 為了協助您區分自訂程式碼與產生的程式碼，以及避免檔案命名衝突，請將自訂程式碼檔案放在不同的子資料夾中。

#### <a name="to-create-the-code-files"></a>若要建立程式碼檔案

1. 在**方案總管**中，以滑鼠右鍵按一下**DSL**專案，指向 [**加入**]，然後按一下 [**新增資料夾**]。 將新資料夾命名為 `CustomCode`。

2. 以滑鼠右鍵按一下新的 [ **CustomCode** ] 資料夾，指向 [**加入**]，然後按一下 [**新增專案**]。

3. 選取 [程式**代碼**檔案] 範本，將**名稱**設定為 `NamespaceTrackingProperty.cs`，然後按一下 **[確定]** 。

     隨即會建立並開啟 NamespaceTrackingProperty.cs 檔案以供編輯。

4. 在資料夾中，建立下列程式碼檔案： `ExampleModel.cs,``HelperClasses.cs`、`Serialization.cs`和 `TypeDescriptor.cs`。

5. 在**DslPackage**專案中，同時建立 `CustomCode` 資料夾，並將 `Package.cs` 程式碼檔案加入其中。

## <a name="adding-helper-classes-to-support-tracking-properties"></a>加入 Helper 類別以支援追蹤屬性
 在 HelperClasses.cs 檔案中，新增 `TrackingHelper` 和 `CriticalException` 類別，如下所示。 稍後在本逐步解說中，您將會參考這些類別。

#### <a name="to-add-the-helper-classes"></a>若要加入 helper 類別

1. 將下列程式碼新增至 HelperClasses.cs 檔案。

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>新增自訂類型描述元的自訂程式碼
 為 `ExampleModel` 網域類別的型別描述項，執行 `GetCustomProperties` 方法。

> [!NOTE]
> DSL 工具針對 `ExampleModel` 呼叫的自訂類型描述元產生的程式碼 `GetCustomProperties`;不過，DSL 工具不會產生可執行方法的程式碼。

 定義這個方法會建立命名空間追蹤屬性的追蹤屬性描述元。 此外，提供追蹤屬性的屬性，可讓 [**屬性**] 視窗正確地顯示內容。

#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>若要修改 Examplemodel.store.customer 網域類別的類型描述元

1. 將下列程式碼新增至 TypeDescriptor.cs 檔案。

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>新增封裝的自訂程式碼
 產生的程式碼會定義 ExampleElement 網域類別的類型描述提供者;不過，您必須加入程式碼，指示 DSL 使用此類型描述提供者。

#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>若要將 DSL 套件更新為使用您的自訂類型描述元

1. 將下列程式碼新增至 Package.cs 檔案。

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-model"></a>加入模型的自訂程式碼
 為 `ExampleModel` 網域類別執行 `GetCustomElementsValue` 方法。

> [!NOTE]
> DSL 工具針對 `ExampleModel` 呼叫所產生的程式碼 `GetCustomElementsValue`;不過，DSL 工具不會產生可執行方法的程式碼。

 定義 `GetCustomElementsValue` 方法會為 `ExampleModel`的 CustomElements 計算屬性提供邏輯。 這個方法會計算具有「命名空間追蹤」屬性（具有使用者更新值）的 `ExampleElement` 網域類別數目，並將表示此計數的字串當做模型中的總元素數的比例傳回。

 此外，將 `OnDefaultNamespaceChanged` 方法加入 `ExampleModel`，並覆寫 `ExampleModel` 之 `DefaultNamespacePropertyHandler` 嵌套類別的 `OnValueChanged` 方法，以呼叫 `OnDefaultNamespaceChanged`。

 因為 DefaultNamespace 屬性是用來計算命名空間追蹤屬性，`ExampleModel` 必須通知 DefaultNamespace 值已變更的所有 `ExampleElement` 網域類別。

#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>修改追蹤屬性的屬性處理常式

1. 將下列程式碼新增至 ExampleModel.cs 檔案。

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-for-the-tracking-property"></a>加入追蹤屬性的自訂程式碼
 將 `CalculateNamespace` 方法加入 `ExampleElement` 網域類別。

 定義此方法會為 `ExampleModel`的 CustomElements 計算屬性提供邏輯。 這個方法會計算具有「命名空間追蹤」屬性（在使用者狀態更新）中的 `ExampleElement` 網域類別數目，並傳回表示此計數的字串，做為模型中的總專案數比例。

 此外，新增、和方法的儲存體，以取得和設定 `ExampleElement` 網域類別的命名空間自訂儲存體屬性。

> [!NOTE]
> DSL 工具針對 `ExampleModel` 所產生的程式碼會呼叫 get 和 set 方法;不過，DSL 工具不會產生可執行方法的程式碼。

#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>若要加入自訂類型描述元的方法

1. 將下列程式碼新增至 NamespaceTrackingProperty.cs 檔案。

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-to-support-serialization"></a>新增自訂程式碼以支援序列化
 加入程式碼以支援 XML 序列化的自訂後置載入行為。

> [!NOTE]
> DSL 工具產生的程式碼會呼叫 `OnPostLoadModel` 和 `OnPostLoadModelAndDiagram` 方法;不過，DSL 工具不會產生可執行這些方法的程式碼。

#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>若要加入程式碼以支援自訂的後置載入行為

1. 將下列程式碼新增至 Serialization.cs 檔案。

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="testing-the-language"></a>測試語言
 下一個步驟是在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 的新實例中建立並執行 DSL 設計工具，以便驗證追蹤屬性是否正常運作。

#### <a name="to-exercise-the-language"></a>若要練習語言

1. 在 [建置] 功能表上，按一下 [重建方案]。

2. 按一下 [偵錯] 功能表上的 [開始偵錯]。

     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 的實驗性組建會開啟包含空白測試檔案的「**調試**程式」方案。

3. 在**方案總管**中，按兩下 trackingPropertyDsl 檔案，在設計工具中開啟該檔案，然後按一下設計介面。

     請注意，在圖表的 [**屬性**] 視窗中，[**預設命名空間**] 屬性為 [ **DefaultNamespace**]，而 [**自訂元素**] 屬性為**0/0**。

4. 將 [ **ExampleElement** ] 元素從 [**工具箱**] 拖曳至圖表介面。

5. 在專案的 [**屬性**] 視窗中，選取 [**元素命名空間**] 屬性，並將值從**DefaultNamespace**變更為**OtherNamespace**。

     請注意，**元素命名空間**的值現在會以粗體顯示。

6. 在 [**屬性**] 視窗中，以滑鼠右鍵按一下 [**元素命名空間**]，然後按一下 [**重設**]。

     屬性的值會變更為**DefaultNamespace**，而此值會以一般字型顯示。

     再次以滑鼠右鍵按一下 [**元素命名空間**]。 現在已停用**重設**命令，因為屬性目前處於追蹤狀態。

7. 將另一個**ExampleElement**從 [**工具箱**] 拖曳至圖表介面，並將其**元素命名空間**變更為 [ **OtherNamespace**]。

8. 按一下設計介面。

     在圖表的 [**屬性**] 視窗中，**自訂元素**的值現在是**1/2**。

9. 將圖表的**預設命名空間**從**DefaultNamespace**變更為**NewNamespace**。

     第一個專案的**命名空間**會追蹤**預設命名空間**屬性，而第二個元素的**命名空間**會保留其使用者更新的**OtherNamespace**值。

10. 儲存方案，然後關閉實驗性組建。

## <a name="next-steps"></a>後續步驟
 如果您打算使用一個以上的追蹤屬性，或在多個 DSL 中執行追蹤屬性，您可以建立文字模板來產生支援每個追蹤屬性的通用程式碼。 如需文字模板的詳細資訊，請參閱程式[代碼產生和 T4 文字模板](../modeling/code-generation-and-t4-text-templates.md)。

## <a name="see-also"></a>另請參閱
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor> <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)[如何：建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)[逐步解說：自訂特定領域語言定義](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)
