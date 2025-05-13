
# crowd

// Crowdfunding UI Redesign - React + Tailwind

import React from "react";
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { motion } from "framer-motion";

const campaigns = [
  {
    id: 1,
    title: "Clean Water for All",
    description: "Help us bring clean water to remote villages.",
    thumbnail: "https://via.placeholder.com/150",
    funded: 60,
    goal: 100,
    daysLeft: 12,
  },
  {
    id: 2,
    title: "Tech for Education",
    description: "Support online learning in underprivileged communities.",
    thumbnail: "https://via.placeholder.com/150",
    funded: 35,
    goal: 80,
    daysLeft: 8,
  },
];

function HeroSection() {
  return (
    <section className="bg-blue-900 text-white py-20 px-4 text-center">
      <motion.h1
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 1 }}
        className="text-4xl md:text-6xl font-bold"
      >
        Empower Innovation. Fund the Future.
      </motion.h1>
      <p className="mt-4 text-xl">A decentralized platform to launch, fund, and grow impactful campaigns.</p>
      <div className="mt-6">
        <Button size="lg">Start a Campaign</Button>
      </div>
    </section>
  );
}

function ValueProposition() {
  return (
    <section className="py-16 px-4 bg-gray-100 text-center">
      <h2 className="text-3xl font-semibold mb-10">Why Choose Us?</h2>
      <div className="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-6xl mx-auto">
        <div>
          <h3 className="text-xl font-semibold mb-2">Decentralized & Transparent</h3>
          <p className="text-gray-600">No intermediaries. All transactions are visible on-chain for complete trust.</p>
        </div>
        <div>
          <h3 className="text-xl font-semibold mb-2">Global Reach</h3>
          <p className="text-gray-600">Reach contributors from all over the world without borders or limits.</p>
        </div>
        <div>
          <h3 className="text-xl font-semibold mb-2">Easy to Use</h3>
          <p className="text-gray-600">Launch your campaign in just a few steps with an intuitive UI and wallet integration.</p>
        </div>
      </div>
    </section>
  );
}

function FeaturedCampaigns() {
  return (
    <section className="py-16 px-4 max-w-6xl mx-auto">
      <h2 className="text-3xl font-semibold mb-8">Featured Campaigns</h2>
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        {campaigns.map((c) => (
          <Card key={c.id} className="rounded-2xl shadow-lg hover:shadow-xl transition">
            <img src={c.thumbnail} alt={c.title} className="w-full h-48 object-cover rounded-t-2xl" />
            <CardContent className="p-4">
              <h3 className="text-xl font-semibold mb-2">{c.title}</h3>
              <p className="text-gray-600 mb-4">{c.description}</p>
              <div className="h-2 bg-gray-200 rounded-full overflow-hidden mb-2">
                <div
                  className="bg-blue-600 h-full"
                  style={{ width: `${(c.funded / c.goal) * 100}%` }}
                ></div>
              </div>
              <p className="text-sm text-gray-500">{c.daysLeft} days left</p>
              <Button className="mt-4 w-full">View Details</Button>
            </CardContent>
          </Card>
        ))}
      </div>
    </section>
  );
}

function HowItWorks() {
  return (
    <section className="py-20 px-4 bg-white text-center">
      <h2 className="text-3xl font-semibold mb-12">How It Works</h2>
      <div className="grid grid-cols-1 md:grid-cols-4 gap-8 max-w-6xl mx-auto">
        <div>
          <span className="text-blue-700 text-4xl">1</span>
          <h3 className="text-xl font-semibold mt-2 mb-1">Connect Wallet</h3>
          <p className="text-gray-600">Securely connect your Web3 wallet to start your journey.</p>
        </div>
        <div>
          <span className="text-blue-700 text-4xl">2</span>
          <h3 className="text-xl font-semibold mt-2 mb-1">Create Campaign</h3>
          <p className="text-gray-600">Set your goal, upload media, and share your story with the world.</p>
        </div>
        <div>
          <span className="text-blue-700 text-4xl">3</span>
          <h3 className="text-xl font-semibold mt-2 mb-1">Raise Funds</h3>
          <p className="text-gray-600">Get contributions from supporters globally and build your vision.</p>
        </div>
        <div>
          <span className="text-blue-700 text-4xl">4</span>
          <h3 className="text-xl font-semibold mt-2 mb-1">Deliver Impact</h3>
          <p className="text-gray-600">Update backers and bring your project to life with transparency.</p>
        </div>
      </div>
    </section>
  );
}

function CallToAction() {
  return (
    <section className="py-20 bg-blue-800 text-white text-center">
      <h2 className="text-3xl md:text-4xl font-semibold">Ready to launch your campaign?</h2>
      <p className="mt-4 text-lg">Join thousands of creators making a difference. Start today.</p>
      <Button size="lg" className="mt-6">Start a Campaign</Button>
    </section>
  );
}

function Footer() {
  return (
    <footer className="bg-gray-900 text-gray-400 py-10 text-center">
      <p className="text-sm">&copy; {new Date().getFullYear()} Decentralized Crowdfunding. All rights reserved.</p>
    </footer>
  );
}

function LandingPage() {
  return (
    <div className="bg-white text-gray-900">
      <HeroSection />
      <ValueProposition />
      <FeaturedCampaigns />
      <HowItWorks />
      <CallToAction />
      <Footer />
    </div>
  );
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<LandingPage />} />
        {/* Future routes: CampaignDetailPage, CreateCampaign, Dashboard */}
      </Routes>
    </Router>
  );
}

export default App;
