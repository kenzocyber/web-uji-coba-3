# web-uji-coba-3
import React, { useState } from "react";
import { motion } from "framer-motion";
import { Star } from "lucide-react";

export default function KenzoPortfolio() {
  const [activeSkill, setActiveSkill] = useState(null);
  const [activeProject, setActiveProject] = useState(null);

  const Rating = ({ stars }) => (
    <div className="flex gap-1 mt-1">
      {[...Array(5)].map((_, i) => (
        <Star
          key={i}
          size={14}
          className={
            i < stars ? "text-yellow-400 fill-yellow-400" : "text-slate-600"
          }
        />
      ))}
    </div>
  );

  // Data Sertifikat
  const certificates = [
    {
      name: "Certified Ethical Hacker (CEH)",
      rate: 5,
      link: "#",
    },
    {
      name: "Offensive Security Certified Professional (OSCP)",
      rate: 5,
      link: "#",
    },
    {
      name: "CompTIA Security+",
      rate: 4,
      link: "#",
    },
    {
      name: "eLearnSecurity Junior Penetration Tester (eJPT)",
      rate: 4,
      link: "#",
    },
    {
      name: "TryHackMe Top 1% Badge",
      rate: 5,
      link: "#",
    },
  ];

  return (
    <div className="min-h-screen w-full bg-gradient-to-b from-slate-900 via-slate-800 to-black text-slate-100 antialiased px-3">
      {/* HEADER */}
      <header className="px-3 py-4">
        <h1 className="text-lg font-bold leading-tight">Kenzo — Ethical Hacker</h1>
        <p className="text-xs text-slate-400">Security Researcher & Pentester</p>
      </header>

      <main className="pb-12 space-y-6">
        {/* HERO */}
        <section className="bg-white/5 rounded-lg p-4 shadow">
          <h2 className="text-base font-bold mb-2">
            Hai, saya Kenzo — <span className="text-indigo-400">Ethical Hacker</span>
          </h2>
          <p className="text-xs text-slate-300 mb-2">
            Saya membantu organisasi menemukan dan menutup celah keamanan dengan pendekatan etis.
          </p>
          <div className="text-xs text-slate-400">
            <div><strong>Email:</strong> pykcyber@gmail.com</div>
            <div>
              <strong>WA:</strong>{" "}
              <a className="underline" href="https://wa.me/6283143490913">+62 831-4349-0913</a>
            </div>
          </div>
        </section>

        {/* SKILLS */}
        <section id="skills">
          <h3 className="text-base font-bold mb-3">Skills</h3>
          <div className="grid grid-cols-1 gap-2">
            {[
              { name: "Web App Pentesting", rate: 5 },
              { name: "API Security", rate: 4 },
              { name: "Network Hardening", rate: 4 },
              { name: "Reverse Engineering", rate: 3 },
              { name: "OSINT & Threat Intel", rate: 5 }
            ].map((skill, i) => (
              <motion.div
                whileTap={{ scale: 0.97 }}
                whileHover={{ scale: 1.02 }}
                key={i}
                onClick={() => setActiveSkill(skill.name)}
                className={`p-2 rounded bg-white/5 border ${
                  activeSkill === skill.name ? "border-indigo-500" : "border-slate-700"
                }`}
              >
                <div className="flex justify-between items-center">
                  <span className="text-xs">{skill.name}</span>
                  <Rating stars={skill.rate} />
                </div>
              </motion.div>
            ))}
          </div>
        </section>

        {/* PROJECTS */}
        <section id="projects">
          <h3 className="text-base font-bold mb-3">Projects</h3>
          <div className="grid grid-cols-1 gap-2">
            {[
              { title: "Enterprise Audit", rate: 5 },
              { title: "Cloud Infra Review", rate: 4 },
              { title: "Bug Bounty Findings", rate: 5 },
              { title: "API Security Hardening", rate: 4 }
            ].map((proj, i) => (
              <motion.div
                whileTap={{ scale: 0.97 }}
                whileHover={{ scale: 1.02 }}
                key={i}
                onClick={() => setActiveProject(proj.title)}
                className={`p-2 rounded bg-white/5 border ${
                  activeProject === proj.title ? "border-emerald-500" : "border-slate-700"
                }`}
              >
                <div className="flex justify-between items-center">
                  <span className="text-xs font-medium">{proj.title}</span>
                  <Rating stars={proj.rate} />
                </div>
              </motion.div>
            ))}
          </div>
        </section>

        {/* CERTIFICATES */}
        <section id="certificates">
          <motion.h3
            className="text-base font-bold mb-3"
            initial={{ opacity: 0, y: 20 }}
            whileInView={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.6 }}
            viewport={{ once: true }}
          >
            Certificates
          </motion.h3>

          <div className="grid grid-cols-1 gap-2">
            {certificates.map((cert, i) => (
              <motion.div
                key={i}
                initial={{ opacity: 0, y: 40 }}
                whileInView={{ opacity: 1, y: 0 }}
                transition={{ duration: 0.6, delay: i * 0.1 }}
                viewport={{ once: true }}
                className="p-3 rounded bg-white/5 border border-slate-700 hover:border-cyan-500 transition-all"
              >
                <div className="flex justify-between items-center mb-1">
                  <span className="text-xs font-medium">{cert.name}</span>
                  <Rating stars={cert.rate} />
                </div>
                <p className="text-[11px] text-slate-400 mb-2">
                  Sertifikat ini saya berikan kepada: <span className="text-cyan-400 font-semibold">Kenzo</span>
                </p>
                <a
                  href={cert.link}
                  target="_blank"
                  rel="noreferrer"
                  className="text-[11px] underline text-indigo-400 hover:text-indigo-300"
                >
                  View Credential
                </a>
              </motion.div>
            ))}
          </div>
        </section>

        {/* CONTACT */}
        <section id="contact" className="bg-white/5 rounded-lg p-4 shadow">
          <h3 className="text-base font-bold mb-2">Contact</h3>
          <a href="mailto:pykcyber@gmail.com" className="block text-xs underline">pykcyber@gmail.com</a>
          <a
            href="https://wa.me/6283143490913"
            target="_blank"
            rel="noreferrer"
            className="block text-xs underline mt-1"
          >
            +62 831-4349-0913
          </a>
        </section>

        {/* FOOTER */}
        <footer className="text-center text-[10px] text-slate-500">
          <div>Website ini dibuat oleh <strong>Kenzo</strong></div>
          <div>© {new Date().getFullYear()} Kenzo. Semua hak cipta dilindungi.</div>
        </footer>
      </main>
    </div>
  );
}
