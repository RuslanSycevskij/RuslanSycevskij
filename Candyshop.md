function buy(dollars, wrappers = 0, pricelist = { d: 1, w: 3 }) {
  const { d, w } = pricelist;
  const d_remainder = dollars % d,
    w_remainder = wrappers % w;
  const candies = (dollars - d_remainder) / d + (wrappers - w_remainder) / w;
  if (!candies) {
    return 0;
  }
  const bonus = buy(d_remainder, w_remainder + candies, pricelist);
  return candies + bonus;
}
console.log(buy(15));
