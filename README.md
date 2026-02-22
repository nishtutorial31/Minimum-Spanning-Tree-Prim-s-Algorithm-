#include <stdio.h>
#define INF 999

int main() {
    int g[3][3] = {
        {0,2,3},
        {2,0,1},
        {3,1,0}
    };

    int selected[3] = {1,0,0};
    int edges = 0, min, x, y;

    while (edges < 2) {
        min = INF;
        for (int i=0;i<3;i++) {
            if (selected[i]) {
                for (int j=0;j<3;j++) {
                    if (!selected[j] && g[i][j]) {
                        if (min > g[i][j]) {
                            min = g[i][j];
                            x = i; y = j;
                        }
                    }
                }
            }
        }
        printf("%d - %d : %d\n", x, y, g[x][y]);
        selected[y] = 1;
        edges++;
    }
    return 0;
}
