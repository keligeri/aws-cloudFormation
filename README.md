# CloudFormation

## Template anatomy
- [Format version](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/format-version-structure.html)
  - There is only one valid version
- Description
- Metadata
- [Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html)
  - Values to pass to your template at runtime (when you create or update a stack). You can refer to parameters from the Resources and Outputs sections of the template.
- [Conditions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/conditions-section-structure.html)
  - Use the optional Parameters section to customize your templates. Parameters enable you to input custom values to your template each time you create or update a stack.
  - You might use conditions when you want to reuse a template that can create resources in different contexts
  - to manipulate 'Resources' or 'Outputs'
- [Transform](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/transform-section-structure.html)
  - for serverless AKA lambda applications
- [Resources](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/resources-section-structure.html)
- [Outputs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/outputs-section-structure.html)
  - Declare output, that you can import into other stack (to create cross.stack references)
  
### [Intrinsic functions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html):
  - !Sub
    ```yaml
      Name: !Sub 
        - www.${Domain}
        - MyTopic-${AlertTopicId}
    ```
  - !FindInMap
    ```yaml
      CurrentAmiId: !FindInMap [ MapName, topLevelKey, SecondLevelKey ] 
    ```
  - !GetAtt
    ```yaml
      EnvironmentType: !GetAtt logicalNameOfResource.attributeName
    ```
