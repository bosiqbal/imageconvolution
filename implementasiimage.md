import numpy as np

# Define the dimensions of the image and filter
image_width = 5   # Replace with actual image width
image_height = 5  # Replace with actual image height
filter_width = 3  # Replace with actual filter width
filter_height = 3 # Replace with actual filter height

# Step 1: Initialize the filter (kernel) H with example values
H = np.array([
    [0, -1, 0],
    [-1, 4, -1],
    [0, -1, 0]
])

# Step 2: Initialize the input image (matrix) X with example values
X = np.random.randint(0, 256, (image_width, image_height))  # Example random image

# Step 3: Initialize the output image (matrix) Y with zeros
Y = np.zeros((image_width, image_height))

# Define the offsets to handle the filter position
offset_x = filter_width // 2
offset_y = filter_height // 2

# Step 4: Implement the convolution algorithm
for x in range(offset_x, image_width - offset_x):
    for y in range(offset_y, image_height - offset_y):
        # Set initial value for the output pixel
        Y[x, y] = 0
        for k1 in range(filter_width):
            for k2 in range(filter_height):
                # Perform the convolution operation
                Y[x, y] += H[k1, k2] * X[x + k1 - offset_x, y + k2 - offset_y]

# Display the input and output images
print("Input Image (X):")
print(X)
print("\nFilter (H):")
print(H)
print("\nOutput Image (Y):")
print(Y)
