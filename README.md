# LearnHub API (json-server)

LearnHub Flutter পরীক্ষার জন্য একটা নকল REST API। সব ডাটা `db.json` ফাইলে, আর [json-server](https://github.com/typicode/json-server) **0.17.4** সেটাকে API হিসেবে চালায়।

> json-server-এর v1 (beta) ব্যবহার করবেন না, তাতে query-এর নিয়ম আলাদা।

## চালানো

Node.js 18 বা তার বেশি লাগবে।

```bash
npm install
npm start
```

অথবা ইনস্টল ছাড়াই:

```bash
npx json-server@0.17.4 --watch db.json --host 0.0.0.0 --port 3000
```

চালু হলে ব্রাউজারে খুলে দেখুন: http://localhost:3000/courses

`--host 0.0.0.0` দেওয়া আছে যাতে একই Wi-Fi-তে থাকা আসল ফোন থেকেও API পাওয়া যায় (`http://<কম্পিউটারের-IP>:3000`)।

## Endpoint

| Method | পাথ | কাজ |
|---|---|---|
| GET | `/categories` | সব ক্যাটাগরি (৪টা) |
| GET | `/courses` | সব কোর্স (১০টা) |
| GET | `/courses?categoryId=2` | নির্দিষ্ট ক্যাটাগরির কোর্স |
| GET | `/courses/3` | একটা কোর্স |
| GET | `/lessons?courseId=3&_sort=order` | একটা কোর্সের লেসন, ক্রম অনুযায়ী |

json-server-এ যেকোনো ফিল্ড দিয়ে ফিল্টার করা যায় (`?fieldName=value`) আর সাজানো যায় (`?_sort=field`)। অচেনা ফিল্ডের নাম দিলে সেটা উপেক্ষা করে সব ডাটা ফেরত দেয়।

## নোট

- Flutter অ্যাপ শুধু GET request করে, তাই `db.json` বদলায় না। প্রতিটা প্রার্থীর পর রিসেট করার দরকার নেই।
- `node_modules/` কাউকে দেওয়ার দরকার নেই, `npm install` আবার বানিয়ে নেবে।
