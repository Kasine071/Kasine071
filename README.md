- 👋 Hi, I’m @Kasine071
- 👀 #include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define HEART_RATE_THRESHOLD 100
#define IMAGE_WIDTH 5
#define IMAGE_HEIGHT 5

int read_heart_rate();
const char* predict_disease(int heart_rate);
void simulate_image_processing();
void print_image(int image[IMAGE_HEIGHT][IMAGE_WIDTH]);


int read_heart_rate() {
    return rand() % 41 + 60; // Random heart rate between 60 and 100
}

const char* predict_disease(int heart_rate) {
    if (heart_rate > HEART_RATE_THRESHOLD) {
        return "High likelihood of Condition X";
    } else {
        return "Low likelihood of Condition X";
    }
}

void simulate_image_processing() {
    int image[IMAGE_HEIGHT][IMAGE_WIDTH] = {
        {120, 130, 140, 150, 160},
        {110, 120, 130, 140, 150},
        {100, 110, 120, 130, 140},
        {90, 100, 110, 120, 130},
        {80,  90, 100, 110, 120}
    };
    
    int threshold = 100;
    printf("\nOriginal Image:\n");
    print_image(image);
    
 
    for (int i = 0; i < IMAGE_HEIGHT; ++i) {
        for (int j = 0; j < IMAGE_WIDTH; ++j) {
            image[i][j] = (image[i][j] > threshold) ? 255 : 0;
        }
    }
    
    printf("\nThresholded Image:\n");
    print_image(image);
}


void print_image(int image[IMAGE_HEIGHT][IMAGE_WIDTH]) {
    for (int i = 0; i < IMAGE_HEIGHT; ++i) {
        for (int j = 0; j < IMAGE_WIDTH; ++j) {
            printf("%3d ", image[i][j]);
        }
        printf("\n");
    }
}

int main() {
    srand(time(NULL)); // Seed the random number generator

    int heart_rate = read_heart_rate();
    printf("Current Heart Rate: %d bpm\n", heart_rate);
    printf("Disease Prediction: %s\n", predict_disease(heart_rate));
    
 
    simulate_image_processing();
    
    return 0;
}
