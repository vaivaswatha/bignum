# bignum

C++ bignum with support for arbitrary precision integer arithmetic.

- wideint arbitrary fixed width signed two's complement or unsigned integer.
- bignum arbitrary variable width signed two's complement or unsigned integer.
- supports static or dynamic width.
- supports arbitrary precision signed and unsigned arithmetic.
- supports operator overloads for C++ math, logical and bitwise operators.
- multiplication and division algorithm from Hacker's Delight.
- divide and conquer algorithm for radix 10 conversion to string.

## Build

The bignum library standard build process uses _cmake_.

#### GCC or Clang on Linux or macOS

```
mkdir build
cd build
cmake -G "Unix Makefiles" ..
```

#### Microsoft Visual Studio 2019 on Windows

```
mkdir build
cd build
cmake -G "Visual Studio 16 2019" ..
```

## Examples

#### Example wideint arithmetic

```
#include <wideint.h>

typedef wideint<256> int256_t;

int main()
{

	int256_t a = 2;
	int256_t b = a | 3;
}
```

#### Example code for C++ bignum arithmetic

```
#include <iostream>

#include <bignum.h>

int main()
{
	bignum x = 2;
	bignum y = x.pow(4096);
	std::cout << y.to_string(10) << std::endl;
}
```

#### Equivalent code using GMP (GNU Multiple Precision Arithmetic Library)

```
#include <iostream>

#include <gmp.h>

int main()
{
	mpz_t result, base;

	mpz_init(base);
	mpz_init(result);
	mpz_set_ui(base, 2);
	mpz_pow_ui(result, base, 4096);

	std::cout << mpz_get_str(NULL, 10, result) << std::endl;

	mpz_clear(base);
	mpz_clear(result);
}
```

## bignum API

bignum implements the following operators and methods:

- bignum(unsigned int n)
- bignum(std::string str, size_t radix)
- bignum& operator+=(const bignum &operand)
- bignum& operator-=(const bignum &operand)
- bignum& operator<<=(int shamt)
- bignum& operator>>=(int shamt)
- bignum& operator&=(const bignum &operand)
- bignum& operator|=(const bignum &operand)
- bignum operator+(const bignum &operand) const
- bignum operator-(const bignum &operand) const
- bignum operator<<(int shamt) const
- bignum operator>>(int shamt) const
- bignum operator&(const bignum &operand) const
- bignum operator|(const bignum &operand) const
- bool operator==(const bignum &operand) const
- bool operator<(const bignum &operand) const
- bool operator!=(const bignum &operand) const
- bool operator<=(const bignum &operand) const
- bool operator>(const bignum &operand) const
- bool operator>=(const bignum &operand) const
- bool operator!() const
- bignum operator*=(const bignum &operand)
- bignum operator/=(const bignum &divisor)
- bignum operator%=(const bignum &divisor)
- bignum operator*(const bignum &operand) const
- bignum operator/(const bignum &divisor) const
- bignum operator%(const bignum &divisor) const
- void from_string(std::string, size_t radix = 0 /*autodetect*/)
- std::string to_string(size_t radix = 10) const
