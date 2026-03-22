import React, { useState, useEffect } from "react";
import { motion } from "framer-motion";

export default function EthicsLab() {
  const [activeTank, setActiveTank] = useState(null);
  const [entscheidung, setEntscheidung] = useState(null);

  useEffect(() => {
    document.body.style.background = "#ffffff";
  }, []);

  const tanks = [
    {
      id: "katze",
      name: "Katze",
      color: "from-pink-400 to-pink-600",
      daten: [
        "Bewusstsein: Komplex",
        "Emotionale Kapazität: Hoch",
        "Menschliche Bindung: Stark",
      ],
      gedanke: "Ich erkenne dein Gesicht. Hilf mir.",
    },
    {
      id: "schmetterling",
      name: "Schmetterling",
      color: "from-blue-400 to-blue-600",
      daten: [
        "Ökologischer Wert: Hoch",
        "Lebensdauer: Kurz",
        "Fragilität: Extrem",
      ],
      gedanke: "Ein Flügelschlag, dann Stille.",
    },
    {
      id: "kakerlake",
      name: "Kakerlake",
      color: "from-green-400 to-green-600",
      daten: [
        "Resistenz: 100%",
        "Anpassungsfähigkeit: Maximum",
        "Schmerzindex: Minimal",
      ],
      gedanke: "Ich war vor dir hier. Ich bleibe nach dir.",
    },
  ];

  if (entscheidung) {
    return (
      <div className="h-screen flex flex-col items-center justify-center text-center">
        <motion.h1
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          className="text-4xl font-semibold mb-6"
        >
          Deine Entscheidung: {entscheidung}
        </motion.h1>
        <p className="text-lg text-gray-600">
          Es gibt keine richtige Antwort. Nur Werte.
        </p>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-gradient-to-b from-white to-gray-100">
      {/* Hero Section */}
      <section className="h-screen flex flex-col items-center justify-center text-center">
        <motion.h1
          initial={{ opacity: 0, y: 40 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1 }}
          className="text-5xl font-bold mb-4"
        >
          The Ethics Lab
        </motion.h1>

        <motion.p
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ delay: 0.5 }}
          className="text-xl text-gray-600"
        >
          Eine Entscheidung. Drei Leben. Was bestimmt den Wert?
        </motion.p>
      </section>

      {/* Tanks */}
      <section className="grid md:grid-cols-3 gap-8 px-10 pb-32">
        {tanks.map((tank) => (
          <motion.div
            key={tank.id}
            whileHover={{ scale: 1.05 }}
            onMouseEnter={() => setActiveTank(tank.id)}
            onMouseLeave={() => setActiveTank(null)}
            className="relative backdrop-blur-xl bg-white/40 p-6 rounded-3xl shadow-xl"
          >
            <div
              className={`h-64 rounded-2xl bg-gradient-to-t ${tank.color} opacity-80`}
            />

            <h2 className="text-2xl mt-4 font-semibold">{tank.name}</h2>

            <div className="mt-3 space-y-1 text-gray-600">
              {tank.daten.map((d, i) => (
                <div key={i}>{d}</div>
              ))}
            </div>

            {activeTank === tank.id && (
              <motion.div
                initial={{ opacity: 0, y: 10 }}
                animate={{ opacity: 1, y: 0 }}
                className="absolute top-4 left-4 right-4 bg-white/70 backdrop-blur-xl p-3 rounded-xl shadow"
              >
                <p className="italic">"{tank.gedanke}"</p>
              </motion.div>
            )}
          </motion.div>
        ))}
      </section>

      {/* Entscheidung */}
      <section className="py-20 text-center">
        <h2 className="text-4xl font-semibold mb-10">Wen rettest du?</h2>

        <div className="flex flex-wrap gap-6 justify-center">
          {tanks.map((tank) => (
            <button
              key={tank.id}
              onClick={() => setEntscheidung(tank.name)}
              className="px-8 py-4 rounded-2xl bg-white shadow-lg hover:shadow-xl transition"
            >
              {tank.name retten
}            </button>
          ))}
        </div>
      </section>
    </div>
  );
}
