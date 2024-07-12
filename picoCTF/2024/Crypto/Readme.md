# Crypto - Easy

## [interencdec](https://play.picoctf.org/practice/challenge/418)

Challenge file has this text - `YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyMHdNakV5TnpVNGZRPT0nCg==`

looks like a base64encoded text, so on decoding got this `b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ=='`

which is again a base64 encoded so did try decoding again which resulted in `wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}`

This seems to be rotated so on RO19 we get the flag

Flag -> `picoCTF{caesar_d3cr9pt3d_f0212758}`
