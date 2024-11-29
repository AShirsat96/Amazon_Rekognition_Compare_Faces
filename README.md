# AWS Face Comparison

A Python implementation for comparing faces between two images using AWS Rekognition. This tool provides detailed similarity analysis and face position information.

## Prerequisites

- Python 3.8.8
- AWS Account with Rekognition access
- AWS Access Key and Secret Key
- boto3 library

## Installation

```bash
pip install boto3
```

## Required Libraries
```python
import boto3
from botocore.exceptions import ClientError, WaiterError
```

## Configuration

```python
aws_accesskey = "Your Access Key"
aws_secretaccess = "Your Secret Access Key"
myregion = "your-region"
```

## Main Function

```python
def Compare_Faces(aws_access, aws_secret, aws_region, Source_Image, Target_Image):
    """
    Compares faces between two images.
    
    Args:
        aws_access: AWS access key
        aws_secret: AWS secret key
        aws_region: AWS region name
        Source_Image: Path to source image file
        Target_Image: Path to target image file
        
    Returns:
        int: Number of matching faces found
        
    Prints:
        Position and similarity percentage for each match
    """
```

## Features

1. Face Comparison:
   - Similarity threshold set to 80%
   - Returns position data for matched faces
   - Provides similarity confidence score
   - Handles multiple faces in images

2. Resource Management:
   - Proper file handling with close operations
   - Error handling for API calls
   - Memory efficient image processing

## Usage Example

```python
matches = Compare_Faces(
    aws_accesskey,
    aws_secretaccess,
    "us-west-2",
    "source_image.jpg",
    "target_image.jpg"
)
```

## Output Format

### Successful Match
```
The face at 0.229 0.076 matches with 99.99% confidence
```

### No Match
Returns 0 (no output printed)

## Response Interpretation

1. Matching Faces:
   - Returns number of matches found (>0)
   - Provides position coordinates
   - Shows similarity percentage

2. Non-Matching Faces:
   - Returns 0
   - No position data printed
   - Indicates no matches above threshold

## Best Practices

1. Image Quality:
   - Use clear, well-lit images
   - Ensure faces are clearly visible
   - Consider image resolution
   - Minimize face occlusion

2. Error Handling:
   - Check file existence
   - Validate image formats
   - Handle API limits
   - Manage file resources

3. Performance:
   - Close file handles properly
   - Consider image size optimization
   - Monitor API usage

## Limitations

1. Similarity Threshold:
   - Fixed at 80%
   - Matches below threshold ignored
   - May need adjustment for specific use cases

2. Image Requirements:
   - Must be readable binary files
   - Faces must be detectable
   - Limited by AWS Rekognition constraints

## Error Cases to Handle

1. File Operations:
   - File not found
   - Permission issues
   - Invalid file formats

2. API Related:
   - Network errors
   - Service limits
   - Authentication failures
