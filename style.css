import React, { useMemo, useState } from "react";
import { createRoot } from "react-dom/client";
import { Calculator, Send, Ruler, Phone, CheckCircle2, Camera } from "lucide-react";
import "./style.css";

const constructionTypes = [
  { id: "partition", label: "Стеклянная перегородка", base: 120, note: "офисы, квартиры, коммерция" },
  { id: "shower", label: "Душевая кабина", base: 160, note: "индивидуальный размер" },
  { id: "railing", label: "Стеклянное ограждение", base: 180, note: "лестницы, балконы, террасы" },
  { id: "canopy", label: "Стеклянный навес", base: 220, note: "входные группы, террасы" },
  { id: "facade", label: "Фасад / витраж", base: 260, note: "алюминий + стеклопакеты" },
];

const glassOptions = [
  { id: "standard", label: "Стандартное стекло", multiplier: 1 },
  { id: "triplex", label: "Триплекс / безопасное", multiplier: 1.25 },
  { id: "energy", label: "Энергоэффективное", multiplier: 1.35 },
  { id: "premium", label: "Премиум / сложная конструкция", multiplier: 1.6 },
];

function App() {
  const [type, setType] = useState("partition");
  const [glass, setGlass] = useState("standard");
  const [width, setWidth] = useState("2.5");
  const [height, setHeight] = useState("2.7");
  const [name, setName] = useState("");
  const [phone, setPhone] = useState("");

  const selectedType = constructionTypes.find((item) => item.id === type);
  const selectedGlass = glassOptions.find((item) => item.id === glass);

  const area = useMemo(() => {
    const w = Number(String(width).replace(",", "."));
    const h = Number(String(height).replace(",", "."));
    if (!w || !h || w <= 0 || h <= 0) return 0;
    return Math.round(w * h * 100) / 100;
  }, [width, height]);

  const price = useMemo(() => {
    if (!area || !selectedType || !selectedGlass) return 0;
    const installation = 1.18;
    const complexity = area < 3 ? 1.15 : area > 12 ? 0.95 : 1;
    return Math.round(area * selectedType.base * selectedGlass.multiplier * installation * complexity);
  }, [area, selectedType, selectedGlass]);

  const message = encodeURIComponent(
    `Здравствуйте! Хочу расчёт DECONA.\n\n` +
    `Город: Одесса\n` +
    `Тип: ${selectedType?.label}\n` +
    `Стекло: ${selectedGlass?.label}\n` +
    `Размер: ${width} м × ${height} м\n` +
    `Площадь: ${area} м²\n` +
    `Ориентир: от ${price} €\n\n` +
    `Имя: ${name || "не указано"}\n` +
    `Телефон: ${phone || "не указан"}`
  );

  const whatsappLink = `https://wa.me/380674833504?text=${message}`;

  return (
    <main className="page">
      <section className="wrap">
        <div className="badge"><Calculator size={15} /> DECONA • Одесса</div>

        <h1>Узнай ориентировочную стоимость стеклянной конструкции</h1>
        <p className="lead">
          Быстрый расчёт для Instagram. Выбери тип, размеры и отправь заявку в WhatsApp.
        </p>

        <div className="card">
          <div className="block">
            <label>1. Тип конструкции</label>
            <div className="options">
              {constructionTypes.map((item) => (
                <button
                  className={type === item.id ? "option active" : "option"}
                  onClick={() => setType(item.id)}
                  key={item.id}
                >
                  <strong>{item.label}</strong>
                  <span>{item.note}</span>
                </button>
              ))}
            </div>
          </div>

          <div className="block">
            <label>2. Размеры</label>
            <div className="sizes">
              <div className="inputBox">
                <span><Ruler size={15} /> Ширина, м</span>
                <input value={width} onChange={(e) => setWidth(e.target.value)} inputMode="decimal" />
              </div>
              <div className="inputBox">
                <span><Ruler size={15} /> Высота, м</span>
                <input value={height} onChange={(e) => setHeight(e.target.value)} inputMode="decimal" />
              </div>
            </div>
            <p className="muted">Площадь: <b>{area || 0} м²</b></p>
          </div>

          <div className="block">
            <label>3. Стекло / сложность</label>
            <select value={glass} onChange={(e) => setGlass(e.target.value)}>
              {glassOptions.map((item) => (
                <option key={item.id} value={item.id}>{item.label}</option>
              ))}
            </select>
          </div>

          <div className="price">
            <span>Ориентировочная стоимость</span>
            <strong>от {price || 0} €</strong>
            <small>Финальная цена зависит от замера, фурнитуры, профиля, монтажа и логистики.</small>
          </div>

          <div className="block">
            <label>4. Контакты для точного расчёта</label>
            <div className="inputBox full">
              <span>Имя</span>
              <input value={name} onChange={(e) => setName(e.target.value)} placeholder="Например, Игорь" />
            </div>
            <div className="inputBox full">
              <span><Phone size={15} /> Телефон</span>
              <input value={phone} onChange={(e) => setPhone(e.target.value)} placeholder="+380..." inputMode="tel" />
            </div>
          </div>

          <a className="whatsapp" href={whatsappLink} target="_blank" rel="noreferrer">
            <Send size={18} /> Отправить заявку в WhatsApp
          </a>

          <p className="photo"><Camera size={16} /> После отправки можно прикрепить фото объекта в WhatsApp.</p>
        </div>

        <div className="benefits">
          <p><CheckCircle2 size={18} /> Расчёт за 30 секунд</p>
          <p><CheckCircle2 size={18} /> Только Одесса</p>
          <p><CheckCircle2 size={18} /> Подходит для ссылки в Instagram</p>
        </div>
      </section>
    </main>
  );
}

createRoot(document.getElementById("root")).render(<App />);
