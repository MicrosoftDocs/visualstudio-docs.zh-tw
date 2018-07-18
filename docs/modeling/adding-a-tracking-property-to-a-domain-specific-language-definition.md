---
title: 在網域指定的語言定義中加入追蹤屬性
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: aec41a7ad2c93d9ad5762f8e4c7e67ea93704f1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953857"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>新增至網域特定領域語言定義的追蹤屬性

本逐步解說示範如何將追蹤屬性新增至網域模型。

A*追蹤網域*屬性是使用者可以更新，但具有預設值所使用的其他網域屬性或項目值計算的屬性。

比方說，在特定領域語言工具 （DSL 工具），網域類別的屬性具有預設值的計算方式是使用的領域類別，而是使用者名稱的顯示名稱可以在設計階段變更的值，或其重設為導出值。

在本逐步解說，您會建立有追蹤都有預設值，根據模型的預設命名空間屬性的屬性命名空間的特定領域語言 (DSL)。 如需追蹤 屬性的詳細資訊，請參閱[定義追蹤之屬性](http://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be)。

-   追蹤屬性描述元 DSL 工具支援。 不過，DSL 設計工具無法用來將追蹤的屬性加入一種語言。 因此，您必須加入自訂程式碼來定義並實作追蹤屬性。

 追蹤屬性具有兩種狀態： 追蹤，並更新使用者。 追蹤屬性有下列功能：

-   在 追蹤狀態，追蹤屬性的值計算，然後更新為變更模型中的其他屬性的值。

-   在更新的使用者狀態的追蹤屬性的值會保留使用者上次設定的屬性值。

-   在**屬性**視窗中，**重設**命令會在更新的屬性時，才會啟用追蹤屬性的使用者狀態。 **重設**命令的追蹤屬性設定為追蹤的狀態。

-   在**屬性**追蹤狀態，其值的追蹤屬性時的視窗會顯示在一般的字型。

-   在**屬性**視窗中，[追蹤] 屬性中更新時由使用者狀態，以粗體字顯示其值。

## <a name="prerequisites"></a>必要條件

您可以開始本逐步解說之前，您必須先安裝這些元件：

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|

## <a name="create-the-project"></a>建立專案

1.  建立特定領域語言設計工具的專案。 將它命名為 `TrackingPropertyDSL`。

2.  在**網域特定語言設計工具精靈**，設定下列選項：

    1.  選取**MinimalLanguage**範本。

    2.  使用預設名稱為特定領域語言， `TrackingPropertyDSL`。

    3.  將模型檔案的檔案副檔名`trackingPropertyDsl`。

    4.  使用模型檔案的預設範本圖示。

    5.  設定要產品名稱`Product Name`。

    6.  設定的公司名稱`Company Name`。

    7.  預設值用於方案中專案的根命名空間`CompanyName.ProductName.TrackingPropertyDSL`。

    8.  可讓精靈以建立組件的強式名稱金鑰檔。

    9. 檢閱之方案的詳細資料，然後按一下**完成**建立 DSL 定義專案。

## <a name="customize-the-default-dsl-definition"></a>自訂預設 DSL 定義
 在本節中，您可以自訂 DSL 定義，以包含下列項目：

-   追蹤模型中的所有元素的屬性命名空間。

-   模型的每個項目，則為 True 的 IsNamespaceTracking 屬性。 這個屬性會指出 [追蹤] 屬性已在追蹤狀態或已更新的使用者狀態。

-   模型的預設命名空間屬性。 這個屬性會用來計算 追蹤屬性的命名空間的預設值。

-   CustomElements 計算模型屬性。 這個屬性會指出項目具有自訂命名空間的比例。

### <a name="to-add-the-domain-properties"></a>若要加入的網域屬性

1.  DSL 設計工具中，以滑鼠右鍵按一下**ExampleModel**網域類別，指向**新增**，然後按一下  **DomainProperty**。

    1.  命名新的屬性`DefaultNamespace`。

    2.  在**屬性**視窗的新的屬性，設定**預設值**至`DefaultNamespace`，並設定**類型**至**字串**。

2.  若要**ExampleModel**網域類別中，加入名為的網域屬性`CustomElements`。

     在**屬性**視窗的新的屬性，設定**種類**至**計算**。

3.  若要**ExampleElement**網域類別中，加入名為的網域屬性`Namespace`。

     在**屬性**視窗的新的屬性，設定**是可瀏覽**至**False**，並設定**種類**至**是 CustomStorage**.

4.  若要**ExampleElement**網域類別中，加入名為的網域屬性`IsNamespaceTracking`。

     在**屬性**視窗的新的屬性，設定**是可瀏覽**至**False**，將**預設值**至`true`，並設定**類型**至**布林**。

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>若要更新的圖表項目和 DSL 詳細資料

1.  DSL 設計工具中，以滑鼠右鍵按一下**ExampleShape**幾何形狀，指向**新增**，然後按一下 **文字裝飾項目的**。

    1.  命名新的文字裝飾項目的`NamespaceDecorator`。

    2.  在**屬性**視窗中的文字裝飾項目，設定**位置**至**InnerBottomLeft**。

2.  DSL 設計工具中選取連接的線條， **ExampleElement**類別**ExampleShape**圖形。

    1.  在**DSL 詳細資料**視窗中，選取**裝飾項目的對應** 索引標籤。

    2.  在**裝飾項目**清單中，選取**NamespaceDecorator**，選取其核取方塊，然後在**顯示屬性**清單中，選取**命名空間**.

3.  在**DSL 總管**，依序展開**網域類別**資料夾中，以滑鼠右鍵按一下**ExampleElement**節點，然後再按一下**加入新網域類型描述元**.

    1.  展開**ExampleElement**節點，然後選取**自訂類型描述元 （網域型別描述項）** 節點。

    2.  在**屬性**視窗中的網域類型描述元，將**自訂編碼**至**True**。

4.  在**DSL 總管**，選取**Xml 序列化行為**節點。

    1.  在**屬性**視窗中，將**自訂 Post Load**至**True**。

## <a name="transform-templates"></a>轉換範本

既然您已如 DSL 定義的網域類別和屬性，您可以確認 DSL 定義可被正確轉換重新產生您的專案的程式碼。

1.  在**方案總管] 中**工具列上，按一下 [**轉換所有範本**。

2.  系統會重新產生方案的程式碼，並將儲存 DslDefinition.dsl。 定義檔案的 XML 格式的相關資訊，請參閱[DslDefinition.dsl File](../modeling/the-dsldefinition-dsl-file.md)。

## <a name="create-files-for-custom-code"></a>建立檔案的自訂程式碼

當您轉換所有範本時，系統會產生 Dsl 和 DslPackage 專案中定義特定領域語言的原始程式碼。 因此，您可以避免干擾所產生的文字，撰寫自訂程式碼所產生的程式碼檔案不同的檔案中。

您必須提供程式碼維護的值與您的追蹤屬性狀態。 若要協助您區別所產生的程式碼中的自訂程式碼，並避免命名衝突的檔案，您的自訂程式碼將檔案放在個別的子資料夾。

1.  在**方案總管] 中**，以滑鼠右鍵按一下**DSL**專案，指向**新增**，然後按一下 [**新資料夾**。 將新的資料夾命名`CustomCode`。

2.  以滑鼠右鍵按一下新**CustomCode**資料夾，指向**新增**，然後按一下 **新項目**。

3.  選取**程式碼檔案**範本，設定**名稱**至`NamespaceTrackingProperty.cs`，然後按一下  **確定**。

     NamespaceTrackingProperty.cs 檔案建立並開啟以供編輯。

4.  在資料夾中，建立下列的程式碼檔： `ExampleModel.cs,``HelperClasses.cs`， `Serialization.cs`，和`TypeDescriptor.cs`。

5.  在**DslPackage**專案中，也建立`CustomCode`資料夾，並將它加入`Package.cs`程式碼檔案。

## <a name="add-helper-classes-to-support-tracking-properties"></a>新增協助程式類別，以支援追蹤內容

將加入到 HelperClasses.cs 檔案中，`TrackingHelper`和`CriticalException`類別，如下所示。 您將會參考這些類別，稍後在本逐步解說。

1.  HelperClasses.cs 檔案中加入下列程式碼。

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>加入自訂程式碼的自訂類型描述元

實作`GetCustomProperties`方法的類型描述元`ExampleModel`網域類別。

> [!NOTE]
> DSL 工具產生的自訂類型描述元的程式碼`ExampleModel`呼叫`GetCustomProperties`; 不過，DSL 工具不會產生程式碼會實作的方法。

定義這個方法會建立追蹤的追蹤屬性的命名空間的屬性描述元。 此外，提供追蹤之屬性的屬性可以讓**屬性**才能正確顯示屬性 視窗。

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>若要修改 ExampleModel 網域類別的類型描述元

1.  TypeDescriptor.cs 檔案中加入下列程式碼。

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

## <a name="adding-custom-code-for-the-package"></a>將自訂程式碼封裝

產生的程式碼定義 ExampleElement 網域類別; 事件類別的類型描述提供者不過，您必須加入程式碼，以指示 DSL，若要使用此類型描述提供者。

1.  Package.cs 檔案中加入下列程式碼。

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

## <a name="add-custom-code-for-the-model"></a>加入自訂程式碼模型

實作`GetCustomElementsValue`方法`ExampleModel`網域類別。

> [!NOTE]
> DSL 工具產生的程式碼`ExampleModel`呼叫`GetCustomElementsValue`; 不過，DSL 工具不會產生程式碼會實作的方法。

定義`GetCustomElementsValue`方法提供邏輯 CustomElements 導出屬性的`ExampleModel`。 這個方法會計算數`ExampleElement`具有追蹤具有使用者已更新的值，並傳回表示這個計數為模型中的總項目所佔百分比的字串屬性的命名空間的網域類別。

此外，新增`OnDefaultNamespaceChanged`方法`ExampleModel`，並覆寫`OnValueChanged`方法`DefaultNamespacePropertyHandler`巢狀類別的`ExampleModel`呼叫`OnDefaultNamespaceChanged`。

因為 DefaultNamespace 屬性用來計算 [追蹤] 屬性中的命名空間`ExampleModel`必須通知所有`ExampleElement`DefaultNamespace 值已變更的網域類別。

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>若要修改追蹤的屬性的屬性處理常式

1.  ExampleModel.cs 檔案中加入下列程式碼。

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

## <a name="add-custom-code-for-the-tracking-property"></a>追蹤屬性加入自訂程式碼

新增`CalculateNamespace`方法`ExampleElement`網域類別。

定義這個方法提供邏輯 CustomElements 導出屬性的`ExampleModel`。 這個方法會計算數`ExampleElement`具有追蹤中已更新的屬性的命名空間的網域類別的使用者狀態，並傳回表示這個計數為模型中的總項目所佔百分比的字串。

此外，新增 取得和設定，命名空間的自訂儲存屬性的方法與存放裝置，`ExampleElement`網域類別。

> [!NOTE]
> DSL 工具產生的程式碼`ExampleModel`呼叫 get 和 set 方法; 不過，DSL 工具不會產生實作方法的程式碼。

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>若要加入自訂類型描述元的方法

1.  NamespaceTrackingProperty.cs 檔案中加入下列程式碼。

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

## <a name="add-custom-code-to-support-serialization"></a>加入自訂程式碼，以支援序列化

加入以支援自訂的後續載入行為進行 XML 序列化程式碼。

> [!NOTE]
> DSL 工具產生呼叫的程式碼`OnPostLoadModel`和`OnPostLoadModelAndDiagram`方法; 不過，DSL 工具不會產生程式碼會實作這些方法。

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>加入程式碼以支援自訂的後續載入行為

1.  Serialization.cs 檔案中加入下列程式碼。

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

## <a name="test-the-language"></a>測試的語言

下一個步驟是要建置和執行 DSL 設計工具中的新執行個體[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，以便您可以確認追蹤屬性是否正常運作。

1.  在**建置**功能表上，按一下 **重建方案**。

2.  按一下 [偵錯] 功能表上的 [開始偵錯]。

     實驗組建[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]開啟**偵錯**方案，其中包含空白的測試檔案。

3.  在**方案總管] 中**，按兩下要在設計工具中，開啟 Test.trackingPropertyDsl 檔案，然後按一下 [設計介面。

     請注意，在**屬性**圖表中，視窗**預設命名空間**屬性是**DefaultNamespace**，而**自訂項目**屬性是**0/0**。

4.  拖曳**ExampleElement**項目從**工具箱**至圖表介面。

5.  在**屬性**視窗項目，選取**元素命名空間**屬性，並將值從變更**DefaultNamespace**至**OtherNamespace**。

     請注意，值**元素命名空間**現在以粗體顯示。

6.  在**屬性**視窗中，以滑鼠右鍵按一下**元素命名空間**，然後按一下 **重設**。

     屬性的值變更為**DefaultNamespace**，和一般字型顯示值。

     以滑鼠右鍵按一下**元素命名空間**一次。 **重設**命令立即停用，因為屬性目前追蹤狀態。

7.  拖曳其他**ExampleElement**從**工具箱**圖表介面，並變更其**元素命名空間**至**OtherNamespace**。

8.  按一下設計介面。

     在**屬性**圖表中，值的視窗**自訂項目**現在**1/2**。

9. 變更**預設命名空間**從圖表**DefaultNamespace**至**NewNamespace**。

     **命名空間**的第一個項目追蹤**預設命名空間**屬性，而**命名空間**第二個項目會保留使用者已更新該值的**OtherNamespace**。

10. 儲存方案，然後關閉 實驗組建。

## <a name="next-steps"></a>後續步驟

如果您想要使用多個追蹤屬性，或在一個以上的 DSL 中實作追蹤屬性，您可以建立文字範本產生一般的程式碼，以支援每個追蹤的屬性。 如需文字範本的詳細資訊，請參閱[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [如何：建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)
