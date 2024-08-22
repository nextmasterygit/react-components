# This is react and nextjs coustom components repository

- Subscribe Next Mastery Youtube Channel for latest Update [nextmastery](https://www.youtube.com/@nextmastery/videos)

## backToTop Component [backtotop](https://github.com/nextmasterygit/react-components/tree/backtotop)

```
"use client";
import Image from "next/image";
import React, { useCallback, useEffect, useState } from "react";

const BackToTop = () => {
  const [height, setHeight] = useState<number>(0);
  const [scrollY, setScrollY] = useState<number>(0);
  const [clientWindow, setClientWindow] = useState<Window>();

  const handleEvent = useCallback(() => {
    setHeight(window.innerHeight);
    setScrollY(window.scrollY);
    setClientWindow(window);
  }, []);

  useEffect(() => {
    window.addEventListener("scroll", handleEvent);
    handleEvent();
    return () => {
      window.removeEventListener("scroll", handleEvent);
    };

    // eslint-disable-next-line react-hooks/exhaustive-deps
  }, []);

  const showArrowTop = scrollY > height ? true : false;
  const handleClick = () => {
    clientWindow?.scrollTo({
      top: 0,
      behavior: "smooth",
    });
  };

  return (
    <button
      onClick={handleClick}
      className={`${
        showArrowTop
          ? "fixed text-black bottom-0 right-0 bg-red-200 hover:bg-red-300 z-50 rounded-full h-6 w-6 mb-10 me-1"
          : "hidden"
      }`}
    >
      <span>
        <Image src={"/arrowhead-up.png"} height={50} width={50} alt="top" />
      </span>
    </button>
  );
};

export default BackToTop;

```

This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
