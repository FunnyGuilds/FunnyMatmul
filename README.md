# FunnyMatmul
Matrix multiplication algorithm in Skript

## Jobs
➡ looking for senior skript developer

What we offer:
- multisport card
- fruit wednesdays

## TODO
Implement `matmut` algorithm in Skript (~ [github.com/FunnyGuilds/FunnyMatmul/plugins/Skript/scripts/matmut.sk](https://github.com/FunnyGuilds/FunnyMatmul/blob/master/plugins/Skript/scripts/matmut.sk)) 

```js
/*
  Example implementation in Panda
*/
module performance

import java.lang.System

class Matmul {

    method Double[][] matgen(Int n) {
        Double[][] a = new Double[n][n]
        Double tmp = 1.0 / n / n

        for (mut Int i = 0; i < n; ++i) {
            for (mut Int j = 0; j < n; ++j) {
                a[i][j] = tmp * (i - j) * (i + j)
            }
        }

        return a
    }

    method Double[][] matmul(Double[][] a, Double[][] b) {
        Int m = a.size()
        Int n = a[0].size()
        Int p = b[0].size()

        Double[][] x = new Double[m][p]
        Double[][] c = new Double[p][n]

        for (mut Int i = 0; i < n; ++i) {
            for (mut Int j = 0; j < p; ++j) {
                c[j][i] = b[i][j];
            }
        }

        for (mut Int i2 = 0; i2 < m; ++i2) {
            for (mut Int j2 = 0; j2 < p; ++j2) {
                mut Double s = 0.0

                for (mut Int k = 0; k < n; ++k) {
                    s = s + (a[i2][k] * c[j2][k])
                }

                x[i2][j2] = s
            }
        }

        return x;
    }

}

main {
    mut Int n = 100

    Matmul m = new Matmul()
    Double[][] a = m.matgen(n)
    Double[][] b = m.matgen(n)
    Double[][] x = m.matmul(a, b)

    System.out.println(x[n / 2][n / 2])
}
```
