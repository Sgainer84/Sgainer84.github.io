# Sophia Gainer Portfolio
/*
Portfolio.jsx — Sophia Gainer
Custom React + Tailwind portfolio connected to GitHub Pages:
https://github.com/Sgainer84/Sgainer84.github.io

Install dependencies before use:
npm install framer-motion lucide-react @shadcn/ui
*/

import React from 'react';
import { motion } from 'framer-motion';
import { GitHub, ExternalLink, Mail } from 'lucide-react';

const meta = {
name: 'Sophia Gainer',
title: 'Cybersecurity Analyst • Quality Engineer',
location: 'Pensacola, Florida',
email: 'sophiagainer84@gmail.com',
resumeUrl: 'https://github.com/Sgainer84/Sgainer84.github.io',
github: 'https://github.com/Sgainer84',
about: `Cybersecurity analyst with 5+ years of experience in wind renewable energy quality engineering and currently completing the Google Cybersecurity Professional Certificate. Experienced in monitoring data systems, managing processes, and responding quickly to irregularities to keep operations safe and efficient. Skilled in Linux, SQL, Splunk, WireShark, Python, and network security tools.`,
};

const projects = [
{
id: 'proj-1',
title: 'TryHackMe Labs & Capture-the-Flag Projects',
desc: 'Hands-on cybersecurity simulations in Linux, Splunk, and Wireshark environments. Practiced vulnerability assessments, log analysis, and network forensics.',
stack: ['Linux', 'Splunk', 'Wireshark', 'CyberChef'],
repo: 'https://tryhackme.com/p/Sgainer84',
demo: null,
},
{
id: 'proj-2',
title: 'Incident Response Dashboard',
desc: 'A custom-built dashboard for visualizing simulated incident responses and log data using Python and SQL for forensic insights.',
stack: ['Python', 'SQL', 'Data Visualization'],
repo: 'https://github.com/Sgainer84/Sgainer84.github.io',
demo: null,
},
{
id: 'proj-3',
title: 'Security Audit Simulation',
desc: 'Completed end-to-end simulated security audits as part of Google Cybersecurity Certificate. Focused on risk identification, NIST/ISO frameworks, and vulnerability reporting.',
stack: ['NIST', 'ISO', 'Risk Management', 'SIEM'],
repo: null,
demo: null,
},
];

function Tag({ children }) {
return (
<span className="inline-block text-sm px-2 py-1 rounded-2xl border border-gray-200 text-sm mr-2 mt-2">{children}</span>
);
}

export default function Portfolio() {
return (
<main className="min-h-screen bg-gradient-to-b from-white to-gray-50 p-6">
<div className="max-w-5xl mx-auto">
{/* Header / Hero */}
<header className="flex flex-col md:flex-row items-start md:items-center justify-between gap-6 mb-8">
<div className="flex items-center gap-4">
<div className="w-20 h-20 rounded-2xl bg-gray-100 flex items-center justify-center p-2 shadow-sm">
<span className="text-xl font-semibold">S</span>
</div>
<div>
<h1 className="text-3xl font-extrabold">{meta.name}</h1>
<p className="text-gray-600">{meta.title} — {meta.location}</p>
</div>
</div>

<div className="flex items-center gap-3">
<a href={meta.resumeUrl} className="inline-flex items-center gap-2 px-4 py-2 rounded-2xl border shadow-sm">Resume</a>
<a href={meta.github} aria-label="GitHub" className="p-2 rounded-2xl border shadow-sm inline-flex items-center">
<GitHub size={18} />
</a>
<a href={`mailto:${meta.email}`} aria-label="Email" className="p-2 rounded-2xl border shadow-sm inline-flex items-center">
<Mail size={18} />
</a>
</div>
</header>

{/* About */}
<section className="bg-white rounded-2xl p-6 shadow-sm mb-8">
<motion.div initial={{ opacity: 0, y: 6 }} animate={{ opacity: 1, y: 0 }} transition={{ delay: 0 }}>
<h2 className="text-xl font-semibold mb-2">About</h2>
<p className="text-gray-700 leading-relaxed">{meta.about}</p>
</motion.div>
</section>

{/* Projects */}
<section>
<h2 className="text-xl font-semibold mb-4">Cybersecurity Projects</h2>
<div className="grid grid-cols-1 sm:grid-cols-2 gap-6">
{projects.map((p) => (
<motion.article key={p.id} className="bg-white rounded-2xl p-4 shadow-sm" whileHover={{ y: -6 }} transition={{ type: 'spring', stiffness: 200 }}>
<h3 className="text-lg font-semibold flex items-center justify-between">
{p.title}
<div className="flex items-center gap-2">
{p.demo && (
<a href={p.demo} className="inline-flex items-center gap-1 text-sm" target="_blank" rel="noreferrer">
Demo <ExternalLink size={14} />
</a>
)}
{p.repo && (
<a href={p.repo} className="inline-flex items-center gap-1 text-sm" target="_blank" rel="noreferrer">
Code <GitHub size={14} />
</a>
)}
</div>
</h3>
<p className="text-gray-600 mt-2">{p.desc}</p>
<div className="mt-3">
{p.stack.map(s => <Tag key={`${p.id}-${s}`}>{s}</Tag>)}
</div>
</motion.article>
))}
</div>
</section>

{/* Contact */}
<section className="mt-8 bg-white rounded-2xl p-6 shadow-sm">
<h2 className="text-lg font-semibold mb-2">Get in touch</h2>
<p className="text-gray-700 mb-4">Interested in collaborating or hiring? Reach out — I respond within a few days.</p>
<a href={`mailto:${meta.email}`} className="inline-flex items-center gap-2 px-4 py-2 rounded-2xl border shadow-sm">Email me</a>
</section>

{/* Footer */}
<footer className="text-center text-sm text-gray-500 mt-8">
<p>Built by Sophia Gainer — <a href={meta.github} className="underline">GitHub</a></p>
</footer>
</div>
</main>
);
}
