import React from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";

const posts = [
  {
    id: 1,
    title: "Getting Started with React",
    category: "Development",
    content: "React is a JavaScript library for building user interfaces...",
    author: "Jane Doe",
  },
  {
    id: 2,
    title: "Healthy Living Tips",
    category: "Lifestyle",
    content: "Healthy living involves more than just diet and exercise...",
    author: "John Smith",
  },
];

export default function BlogHomePage() {
  return (
    <div className="p-6 max-w-5xl mx-auto">
      <h1 className="text-4xl font-bold mb-6 text-center">My Blog</h1>
      <Tabs defaultValue="all" className="mb-6">
        <TabsList>
          <TabsTrigger value="all">All</TabsTrigger>
          <TabsTrigger value="Development">Development</TabsTrigger>
          <TabsTrigger value="Lifestyle">Lifestyle</TabsTrigger>
        </TabsList>
        <TabsContent value="all">
          <PostList posts={posts} />
        </TabsContent>
        <TabsContent value="Development">
          <PostList posts={posts.filter((post) => post.category === "Development")} />
        </TabsContent>
        <TabsContent value="Lifestyle">
          <PostList posts={posts.filter((post) => post.category === "Lifestyle")} />
        </TabsContent>
      </Tabs>
      <NewPostForm />
    </div>
  );
}

function PostList({ posts }) {
  return (
    <div className="grid gap-4">
      {posts.map((post) => (
        <Card key={post.id} className="hover:shadow-lg transition-shadow">
          <CardContent className="p-4">
            <h2 className="text-xl font-semibold mb-2">{post.title}</h2>
            <p className="text-sm text-gray-500 mb-1">Category: {post.category}</p>
            <p className="text-gray-700 mb-2">{post.content}</p>
            <p className="text-sm text-gray-600 italic">Author: {post.author}</p>
          </CardContent>
        </Card>
      ))}
    </div>
  );
}

function NewPostForm() {
  return (
    <div className="mt-10">
      <h2 className="text-2xl font-semibold mb-4">Write a New Post</h2>
      <form className="grid gap-4">
        <Input placeholder="Title" />
        <Input placeholder="Category" />
        <Textarea placeholder="Content" rows={5} />
        <Input placeholder="Author" />
        <Button type="submit">Publish</Button>
      </form>
    </div>
  );
}
