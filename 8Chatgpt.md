import React, { useState } from "react";
export default function App() {
  const [task, setTask] = useState("");
  const [list, setList] = useState([]);
  return (
    <div>
      <input
        value={task}
        onChange={(e) => setTask(e.target.value)}
      />
      <button
        onClick={() => {
          if (task) {
            setList([...list, { text: task, done: false }]);
            setTask("");
          }
        }}
      >
        Add
      </button>
      {list.map((t, i) => (
        <div key={i}>
          <span
            onClick={() =>
              setList(
                list.map((x, j) =>
                  j === i ? { ...x, done: !x.done } : x
                )
              )
            }
            style={{
              textDecoration: t.done ? "line-through" : "none",
              cursor: "pointer"
            }}
          >
            {t.text}
          </span>
          <button
            onClick={() =>
              setList(list.filter((_, j) => j !== i))
            }
          >
            Delete
          </button>
        </div>
      ))}
    </div>
  );
}
